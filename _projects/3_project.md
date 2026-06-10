---
layout: page
title: PUZZLE
description: Proximity-based Unsupervised Zonal Zones Learnable Embeddings for the province of Zuid-Holland
img: assets/img/spatial_proxi.jpg
importance: 1
category: work
related_publications: false
---

## Introduction

This document defines the conceptual framework and design choices behind **PUZZLE (Proximity-based Unsupervised Zonal Zones Learnable Embeddings)**, a method for learning compact, informative latent representations of geographic regions in the Province of Zuid-Holland from high-dimensional spatial data. Before diving into technical details, I couldn't resist being extra and adding some philosophy why this work had me excited.

## Philosophy

This project comes from a way of thinking about policy-making as an approximation problem, not a rule-making one. All kind of policies are built under uncertainty and are highly subjective to the eye of the beholder. 

Assume the real world can be thought of as an unknown state space $$ \mathcal{W} $$. What decision-makers actually observe is not $$ \mathcal{W} $$ itself, but some projection of it, $$ \mathcal{D} = f(\mathcal{W}) $$. The function $$ f $$ reflects practical constraints: what can be measured, what data exists, and what people agree is meaningful. Policies then act as mappings $$ \pi : \mathcal{D} \rightarrow \mathcal{A} $$, turning observations into actions.

In practice, policy systems lean heavily on **semantic structure** (zones, regions, categories, labels) because they’re easy to communicate and reason about. The underlying structure of $$ \mathcal{W} $$ ends up being represented by boundaries we define, rather than relationships that emerge on their own. We are transforming a complex world into the language domain and this transformation is imperfect and lossy by nature.

Data-driven approaches move things closer to observation by relying on measurable signals, but they still operate within a limited feature space $$ \mathcal{X} \subseteq \mathcal{W} $$. That space is shaped by what’s observable and interpretable, so learning naturally gravitates toward familiarities. There are these baked-in assumptions coming from our vision of the world, but what if we could break free from them?

The idea explored here is a shift in how we represent space and structure. We want to move out of the language domain and into a mathematical one. In these spaces, similarity is something you infer, not something you name.

This perspective leads to **PUZZLE**, a continuous embedding of geographic space directly from measurable spatial signals, without predefined zones or human-assigned labels. They emerge implicitly through proximity and interaction in the embedding space.

From this viewpoint, geography isn’t a set of regions with names, it’s a latent manifold. PUZZLE is an attempt to learn that manifold directly from data, and to let structure show up where the data says it should.

## Problem Statement

Ok, the goal is pretty simple: we want to learn compact, informative latent representations of geographic regions in the Province of Zuid-Holland from any dataset that includes spatial information. 

The province is discretized into a regular **H3 hexagonal grid**. Each hexagon is treated as a discrete spatial token.

Let

$$
\mathcal{H} = \{h_1, \dots, h_N\}
$$

denote the set of H3 cells.Furthermore each $$h_i$$ has a neighborhood $$\mathcal{N}(h_i)$$ defined by geographic adjacency in the H3 grid of rank 1. The objective here is to **learn a representation**

$$
f_\theta : \mathbb{R}^F \rightarrow \mathbb{R}^D
$$

Or in words:

> Find an embedding that compresses redundant information, respects spatial structure, is reusable across downstream task and such that any potential relationships between regions are preserved in latent space.

---

## Core Design Choice 1: Redundancy Reduction

The absolute first problem we need to tackle is the encoding of overlapping information in $$x_i$$. Each cell $$h_i$$ is associated with a feature vector $$x_i \in \mathbb{R}^F$$, where the components of $$x_i$$ are often highly correlated (trees and squirrels in a unit). Traditional rule-based approaches attempt to map these features to semantic categories via expert-defined functions. However, we discard any manual intervention or rule-based approaches since this automatically introduces language biases.
 
The core idea is that we want to be able to add any kind of data, and the model should remain useful without human intervention or feature engineering. This is achieved through **redundancy reduction**: encouraging the model to learn representations that minimize overlap in information across dimensions, rather than memorizing or amplifying correlated inputs.

Let us denote the raw feature covariance by:

$$
\Sigma_x = \mathbb{E}[x x^\top],
$$

which in realistic spatial datasets is typically far from diagonal, reflecting strong correlations and shared structure in the input space.

The goal of redundancy reduction is to learn representations $$z_i \in \mathbb{R}^D$$ whose components are:

- **decorrelated**, so dimensions do not encode the same signal  
- **equally informative**, so no single dimension dominates  
- **non-degenerate**, so the representation does not collapse to trivial solutions  

In practice, redundancy reduction is enforced by minimizing cross-correlation between embedding dimensions across paired views of the data, encouraging the empirical cross-correlation matrix to approach the identity:

$$
C \approx I.
$$

where $$C \in \mathbb{R}^{D \times D}$$ is the empirical cross-correlation matrix between embedding dimensions computed over paired views of the data. A key consequence of redundancy reduction is that it makes the representation stable under the addition of new data. Suppose the input space is extended from $$x \in \mathbb{R}^F$$ to

$$
x' = \begin{bmatrix} x \\ y \end{bmatrix} \in \mathbb{R}^{F+K},
$$

where $$y \in \mathbb{R}^K$$ contains additional features. These new features may be redundant with existing ones, partially overlapping, or genuinely novel. Because redundancy reduction enforces balanced variance and low mutual information across embedding dimensions, the representation cannot simply stack new signals on top of existing ones. Instead:

- If $$y$$ is redundant with $$x$$, its information is compressed into existing latent directions without changing the overall structure.
- If $$y$$ is partially novel, information is redistributed through a rotation of the latent basis while preserving decorrelation.
- If $$y$$ introduces a genuinely new factor of variation, it is forced to occupy previously unused capacity in the latent space, provided sufficient dimensionality.

---

## Core Design Choice 2: Spatial Proximity as Supervision

The model is trained without labels. The only supervision signal arises from **geographic adjacency**. Okay, Okay, this is based on a human assumption and kind of undermines the concept of getting rid of human biases but I think this is a reasonable one. Neighbouring regions tend to share similar characteristics due to shared planning policies, infrastructure, and land-use context. To formalize the assumption:

For each cell $$h_i$$, we sample a neighboring cell

$$
h_j \sim \mathcal{N}(h_i)
$$

and form a training pair $$(x_i, x_j)$$.

Then:

Let each cell $$h_i$$ be associated with a spatial coordinate $$p_i \in \mathbb{R}^d$$. The embedding is constructed such that smaller spatial distance between cells corresponds to smaller distance between their embeddings. Formally, for any pairs $$(i,j)$$ and $$(k,\ell)$$:

$$
\lVert p_i - p_j \rVert \;\le\; \lVert p_k - p_\ell \rVert
\;\Rightarrow\;
\lVert z_i - z_j \rVert \;\le\; \lVert z_k - z_\ell \rVert.
$$

This does assume uniformity among neighbors, but we could hope for the law of large numbers to kick in.

---

## Core Design Choice 3: Hyperspherical Geometry

A central geometric choice is to remove vector magnitude as a degree of freedom. The goal is to make the representation purely directional, so that geometry is driven by angles, and downstream “transformations” can be expressed as movements along a curved manifold.

Let $$z_i \in \mathbb{R}^D$$ be the raw embedding produced by the encoder. We apply per-sample normalization to obtain the effective representation

$$
\hat z_i = \frac{z_i}{\|z_i\|}.
$$

By construction,

$$
\|\hat z_i\| = 1
\qquad \Rightarrow \qquad
\hat z_i \in \mathbb{S}^{D-1}.
$$

This removes scale as a representational channel: semantic information cannot be stored in the norm, only in the direction of $$\hat z_i$$. As a result:

- Similarity is naturally measured via cosine similarity:
  $$
  \hat z_i^\top \hat z_j = \cos(\angle(\hat z_i,\hat z_j)).
  $$
- Representations become scale-invariant and comparable across regions.
- Policy interventions can be interpreted as directional shifts on the hypersphere (i.e., updates in the tangent space projected back onto $$\mathbb{S}^{D-1}$$).

Geometrically, the model learns a **direction field over geographic space**, where each direction corresponds to a latent spatial type.

---
## In Practice

Ok, getting off paper territory. I received internal data to validate the concept, I designed a method to model every point and polygon to the H3 grid and created a pipeline to extract features from the raw data. Furthermore I scraped satellite imagery and used a basic CNN to extract image features for each cell as well.


Training was made possible by an ECC Grant for this concept in the form of GPU credits, so I had a fully functional environment to test this idea.

We managed to extract the full Province of Zuid-Holland into a grid of H3 cells at resolution 9 and extracted the representations after training. The embeddings were then used for multiple tasks:

- The land-use passport (Aligning the embeddings with the primary land-use types defined by the province (residential, agricultural, natural, industrial, etc.)) scoring based upon a semantic set. We first used some manual labeled land-use types to transfer from latent space to language space and then scored the rest of the cells based on the collective distance/a small MLP approach.
- Twin analysis (Finding similar regions across the province for policy benchmarking)
- Clustering analysis (Finding emergent zones based on embedding similarity for regional planning)

Then life happened: we got permission to increase capacity on the AI team at the Province of Zuid-Holland, so the primary focus switched and the project was delayed.


---

## Great minds think alike

The idea of PUZZLE was a composition of existing ideas but novel in its overall approach. Then came the big news:

https://deepmind.google/blog/alphaearth-foundations-helps-map-our-planet-in-unprecedented-detail/

DeepMind recently introduced **AlphaEarth Foundations**, a method for learning latent representations of geographic regions from high-dimensional spatial data, using redundancy reduction and proximity-based supervision. The similarities between PUZZLE and AlphaEarth Foundations are big, from the core design choices to the underlying philosophy, supporting and validating the approach.

