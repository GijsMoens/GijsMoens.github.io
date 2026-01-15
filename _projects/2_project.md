---
layout: page
title: Resolution Invariant Image Segmentation for Tumor Detection
description: A research project in collaboration with the NKI.
img: assets/img/medical_segmentation.jpg
importance: 1
category: work
related_publications: true
---

# The goal

This project has a funny origin story. During one of the *borrels* (drinks), one of the colleagues at the Netherlands Cancer Institute (NKI) told me about the impressive work they had been doing on tumor segmentation using deep learning.

However they were dealing with images coming from different scanners, hospitals, and protocols. Same anatomy, same disease but wildly different resolutions. Models trained on one dataset would silently degrade on another. Sometimes badly. The usual fixes applied: resampling everything to a canonical resolution, aggressive augmentation, multi-scale tricks. All of them helped a bit, none of them solved the core issue. A surprisingly annoying practical problem but what bothered me most was that this problem felt artificial:

A tumor does not suddenly change shape because a scanner has smaller voxels. The physics of the image is continuous. The pathology is continuous. Only our representation, or in other words the pixels on a grid, are discrete. So we were asking convolutional neural networks to learn invariance to something we introduced ourselves.

So the goal of the project slowly crystallized into something more fundamental:

> Can we build an image segmentation model whose parameters do **not depend on image resolution**, and where changing resolution is nothing more than sampling the *same underlying operator* more or less densely?

In other words: stop learning in pixel space, start learning in *physical space*.

---

# Why standard convolutions struggle

Let’s briefly look at why this is hard with standard CNNs.

A convolutional layer applies a discrete kernel $$ k \in \mathbb{R}^{K \times K} $$ over a discrete grid:

$$y[i,j] = \sum_{u,v} k[u,v] \; x[i-u, j-v]$$

This kernel is defined **on the pixel grid**. If you change the resolution, the physical meaning of that kernel changes. A ($$3 \times 3$$) kernel at 0.5 mm spacing covers a very different region of tissue than the same kernel at 1.5 mm spacing.

You can resample the image, but now you are interpolating data before the network sees it, baking assumptions into preprocessing rather than into the model itself.

Architecturally, CNNs try to compensate by stacking layers. But stacking layers just increases the effective receptive field, not the physical consistency of what is learned. The kernel is still defined on a grid.

So resolution invariance is at best learned implicitly, and at worst not learned at all.

{% include figure.liquid loading="eager" path="assets/img/resolution_dependence.jpg" title="The problem of kernel convolution" class="img-fluid rounded z-depth-1" %}

---

# Why not transformers?

Transformers have been proposed as a solution to this problem. Since they operate on sets of patches, they can in principle handle varying resolutions more gracefully. However, transformers come with their own set of challenges:

- **Computational complexity**: The self-attention mechanism scales quadratically with the number of patches, making it computationally expensive for high-resolution images.
- **Lack of inductive bias**: Transformers lack the strong inductive biases present in CNNs, which can be beneficial for learning spatial hierarchies in images.

Transformers make (some) sense for semantic understanding of images but don't feel suitable for precise tasks like medical image segmentation.

---

# Mamba

One morning in the metro, I read the article about Mamba, the thing that stuck with me was the conceptual shift which was so obvious compared to transformers. Text should be sequential since language is sequential and that led me thinking about vision. Convolution is reasonable but only if we're able to learn global, invariant structures. I feel like vision is not about you knowing every objet from every perspective, it's fundamentally about recognizing structures that are invariant to resolution, orientation, and scale. If we are able to learn those structures, we can generalize far better.

# The bit naive idea:

What if, instead of learning a full 2D convolutional kernel directly, we decomposed it into a combination of horizontal and vertical signals, and then recombined those to form the 2D operator (the S4ND approach).

This immediately gives us a few nice properties. First, it’s resolution invariant: we’re learning complex-valued functions defined in continuous space, which we can discretize on whatever grid the data happens to live on. Second, the kernel becomes *global* almost for free, its effective complexity scales like  $$\mathcal{O}(H + W)$$ rather than $$\mathcal{O}(HW)$$.

which means we can cover the entire image without paying a quadratic cost.

We started running experiments with this idea and, somewhat to our surprise, it worked very well. The effect was especially strong in medical imaging, where anatomy and pathology tend to exhibit a lot of coherent structure along horizontal and vertical directions.

There was just this one problem, not all kernels of interest are decomposable along our unit directions. Edges and elongated structures can appear at any angle, and our model struggled to capture those. Think of a vessel running diagonally through tissue, or the boundary of a tumor that’s not aligned with the axes. Our model had no way to represent those orientations effectively.

# Moving to the frequency domain

When reading into the laplace transform (given as a trick in S4ND), I realized that the 
concept of S4ND could be generalized to arbitrary orientations if we don't align based on axes but learn them. This led to the idea of working in the frequency domain.

For a continuous signal $$ x : \mathbb{R}^D \to \mathbb{C}^{C_{\text{in}}} $$, a linear, shift-invariant operator can always be written as a convolution:

$$y(x) = \int_{\mathbb{R}^D} k(x - z) \, x(z) \, dz$$

The key observation is that convolution becomes *multiplication* in the Fourier domain:

$$\widehat{y}(\omega) = \widehat{k}(\omega)\,\widehat{x}(\omega)$$

Here, $$ \widehat{k}(\omega) $$ is the **frequency response** of the operator. This object completely characterizes the convolution and it lives in **continuous frequency space**.

If we define $$ \widehat{k}(\omega) $$ as a continuous function, then resolution disappears from the parameters. Resolution only determines **which frequency grid we use**.

Formally, let

$$ \widehat{H}_\theta : \mathbb{R}^D \to \mathbb{C}^{C_{\text{out}} \times C_{\text{in}}} $$

be a continuous spectral operator. Given any discretization $$(N, \Delta)$$, we simply evaluate it on the corresponding DFT grid:

$$ \widehat{y}_{(N,\Delta)}(\omega_n) = \widehat{H}_\theta(\omega_n)\,\widehat{x}_{(N,\Delta)}(\omega_n) $$

Note that the full spectral operator is not dependent on the parameters. For any resolution or sample interval we use the same parameters, only a different grid. **True resolution invariance.**

---

# The Spectral Operator

This idea is not new. Fourier Neural Operators, global filters, and related methods already operate in the frequency domain. But most of them parameterize the spectrum **discretely**:

- A learned complex mask per frequency
- Or a fixed set of low-frequency coefficients tied to FFT indices

The moment you change resolution, those indices change. The operator itself changes.

Other approaches learn $$\widehat{H}(\omega)$$ using an MLP over $$ \omega $$. That gives continuity, but at a price:

- No structure
- No orientation bias
- Training instability
- Poor parameter efficiency

 Images are full of oriented structure: edges, ignoring orientation in frequency space is throwing away useful inductive bias.

So the question became:

> Can we define a **structured, continuous, orientation-aware spectral operator** that stays resolution invariant by construction?

---

# Building structured spectral modes

The trick was to stop learning the full spectrum directly, and instead build it from a **small set of orientated spectral modes**.

Instead of taking the two axis-aligned orientations, we choose M learnable orientations on a N-Dimensional sphere. Each mode is a smooth, analytic function in frequency space. Inspired by linear time-invariant systems (like S4 or Mamba), we parameterize each mode as:

$$ T_m(\omega) = \frac{1}{i\,s_m(\omega \cdot v_m)- a_m + \tau_m \|(I - v_m v_m^\top)\omega\|^2} $$

Where:

- $$ v_m \in \mathbb{R}^D $$: a unit vector defining the **orientation** of the mode  
- $$ s_m > 0 $$: controls **spectral selectivity** along that direction  
- $$ a_m \in \mathbb{C} $$: controls **damping** and **oscillation**  
- $$ \tau_m \ge 0 $$: **penalizes** frequencies orthogonal to $$ v_m $$ 

Geometrically, each mode behaves like a directional filter in frequency space. Structural functions in frequency space where points align.

Instead of learning one giant operator, we learn \( M \) such modes and mix them across channels:

$$ 

\widehat{H}_{k,c}(\omega)
=
\sum_{m=1}^{M}
C_{k m}\, T_m(\omega)\, B_{m c}

$$

This gives us:
- Low-rank structure
- Massive parameter sharing
- Interpretability
- Strong inductive bias

And importantly the entire construction is **continuous in $$ \omega $$**.

---

# Putting it into a segmentation model

A single block looks like this:

1. FFT each input channel
2. Apply the learned spectral operator (by multiplying with $$ \widehat{H}_\theta(\omega)) $$
3. Inverse FFT
4. Add a residual projection
5. Apply nonlinearity

Stack a few of these blocks, add a lightweight head, and you get a fully resolution-invariant segmentation network.

No U-Net pyramids. No patching. No attention maps exploding with resolution.

---

# Does it actually work?

Short answer: yes.

On real 3D medical datasets (KiTS, ACDC, AMOS), the model matches or exceeds nnU-Net performance while using **an order of magnitude fewer parameters** (200x in some cases). Furthermore on external validation datasets performance degrades far less than standard architectures. 
{% include figure.liquid loading="eager" path="assets/img/results_segmentation.jpg" title="The model tumor segmentation" class="img-fluid rounded z-depth-1" %}

Below the left of the two is the nnU-Net, the right is our model. 

{% include figure.liquid loading="eager" path="assets/img/medical_segmentation.jpg" title="The model tumor segmentation" class="img-fluid rounded z-depth-1" %}

 The model remains stable under:
- Rescaling
- Rotation
- Translation
- Noise
- Combined distortions

Currently, we are looking into using the model for computer vision benchmarks as well, testing the limits of this approach.

---

# TL;DR

- We created a resolution invariance convolution operator 
- Global receptive fields without quadratic attention costs
- Strong inductive bias for oriented structures
- Parameters correspond to physical behavior, not grid artifacts

Is it perfect? No.
- FFTs add overhead
- Very fine local detail can still benefit from spatial convolutions
- Hybrid models are probably the future
- Need to see if it holds on computer vision benchmarks

But as a *core operator*, this feels aligned with the physics of imaging rather than arbitrariness of our data representation.

