---
layout: post
title: Why you're incredibly right in being wrong
date: 2025-03-09 14:24:00
description: Where rationality starts to break down.
tags: learning organizations epistemics systems
categories: Weekly-Thoughts Non-Technical
---

There is a tempting explanation for collective failure that reaches for irrationality, bias, or bad intent. But that explanation quietly assumes that people *could* tell they were wrong if they just tried harder.

This article explores a more uncomfortable idea.

Under certain conditions, intelligent systems cannot reliably tell whether they are **correct** or merely **coherent**. Not because they are confused, but because the information required to make that distinction is just not available.

What follows is a deliberately simple, almost toy-level formalization. It uses axioms and propositions, not to sound technical, but to make the limits precise.

---

## A minimal formal setup

We will talk about systems. A system can be a brain, a person, an organization, or a group.

### Definitions

- **World state**  
  The actual state of the world.  
  This includes the unconstrained truth, the oracle.

- **Observations**  
  What the system actually receives, observations is direcltly related to the system (we can observe the same world state differently).  
  Observations can be anything available to system: vision, speach, news, etc.

- **Internal model**  
  The system’s internal representation of how the world works.  
  How the system thinks the world is, how you think things work.

- **Prediction error**  
  The difference between what the model expects and what is observed.  
  The surprise one experiences when something happens that you did not predicted.

- **Correctness**  
  The degree to which the model is aligned with the true world state.

- **Coherence**  
  The degree to which the model is internally consistent and successfully predicts observed signals.

The key distinction is that correctness is defined relative to the world, while coherence is defined relative to the system’s own observations.

---

### Axiom 1: No system has direct access to ground truth

All learning happens through observations.  Sometimes those observations track the world reasonably well, especially in simple sensory contexts. When you touch a hot stove, the signal is immediate and hard to misinterpret. But as soon as we move beyond direct physical interaction, observations become increasingly incomplete, delayed, and distorted. For instance in social systems:

Someone may agree outwardly while disagreeing internally. The observation is agreement. The underlying world state could be alignment, politeness, resignation, fear, or strategic compliance but from the outside, these states are indistinguishable. The same signal corresponds to multiple realities. In those cases, observations do not uniquely determine the world state. Learning must proceed under ambiguity. Systems cannot update directly toward truth, only toward interpretations that remain consistent with what they are able to observe.

Or in organizational contexts:

A company may track KPIs that appear to improve quarter after quarter. The observation is progress. The underlying world state could be genuine improvement, shifting definitions of success, deferred costs, or growing fragility hidden behind short-term gains. From within the system, these possibilities are hard to tell apart. The signals respond, but not necessarily to what actually matters.

---

### Axiom 2: Biological optimization is based minimizing prediction error

Brains and learning systems reduce prediction error.

Prediction error is not just informational. It is biological. Surprise correlates with arousal, stress, metabolic cost, and effort. Reducing prediction error feels stabilizing and safe.

You pick up a cup of coffee expecting it to be full. You're predicting someones mood based on their facial expression. You drive to work expecting it to take a certain amount of time. Your brain is constantly generating predictions about the world and updating them based on what actually happens. If the coffee was less full, your first joke didn't go as expected or there is road maintanance, your brain experiences prediction error, which motivates you to adjust your expectations or actions to reduce that error in the future.

We call this biological optimization because it is a fundamental drive in living systems to minimize uncertainty (And this is the full principle about AI, now you can call yourself an expert).

---

### Axiom 3: Learning depends on informative feedback

Learning requires that differences in belief or behavior produce differences in what the system experiences. If updating a model does not reliably change the signals the system receives, there is nothing to learn from. The system may continue to act, but it cannot tell whether those actions are better or worse with respect to the underlying world state.

Meaning, when I turn the shower knob, the temperature should change. If it doesn't there is no way to infer whether turning it further will help. Similarly, if I change my communication style in a team but receive no feedback on how it affects collaboration, I cannot learn whether my change was beneficial.

---

### Proposition 1: Low prediction error does not imply correctness

From **Axiom 1** and **Axiom 2**, minimizing prediction error means aligning the model with observations, not with reality itself.

Let's see this in practice:

You make this terrible joke but social norms encourage politeness which leads to observing polite laughter.

**Axiom 1**: You have no way of infering the true world state (the joke was bad) from the observation (people laughed politely).
**Axiom 2**: You minimize prediction error by updating your model to expect polite laughter when you tell that joke.

A model can be internally coherent and predict observations well while being poorly aligned with the true world state (you're not funny but still expect polite laughter in the future).

Therefore, low surprise implies coherence, not correctness.

---

### Proposition 2: When feedback is strong, coherence and correctness correlate

When observations are timely, attributable, and causally linked to the world state, incorrect models generate prediction error.

You can find this:
- In physical environments
- In low-stakes social contexts, where people don’t need to protect themselves.
- In your partner (hopefully)

In these environments, coherence tends to track correctness, because reality pushes back.

---

### Proposition 3: When feedback weakens, correctness becomes unidentifiable

When observations are delayed, noisy, proxy-based, or socially filtered, changes in the world state no longer produce clear changes in observations.

In this case, multiple internal models can generate the same observations.

At this point, **Axiom 3** breaks. Differences in belief or behavior stop producing differences in experience. When this happens, no internal process can distinguish which model is more correct.

Correctness is no longer identifiable from inside the system.

From **Axiom 2**, systems do not stop optimizing when feedback weakens.
They continue minimizing prediction error.

But since prediction error now reflects only internal consistency, optimization shifts from external accuracy to internal coherence.

---

**And there it is:**

---
### Proposition 4: A wrong but stable internal model can dominate a fragile but correct one

A model that is slightly more true to the world model but generates frequent prediction error will feel unstable, effortful, and costly.

A model can be closer to the truth and still lose, simply because it makes the present harder to inhabit. A less correct but highly coherent model will feel calm, fluent, and confident.

Given biological pressure to reduce prediction error, the stable model is often favored.

Thus, a wrong but stable model can feel better than a fragile but correct one.

This increases when systems become social and observations increasingly come from other agents.

Agreement, validation, and shared narratives reduce individual prediction error.

Social coherence replaces environmental feedback.

This creates a positive feedback loop:
- shared expectations reduce surprise,
- reduced surprise increases confidence,
- increased confidence reinforces shared expectations.

The system becomes increasingly coherent while drifting further from reality.

---

## The experiential consequence

From inside the system, none of this feels like failure.

Confidence grows because the system’s outputs agree with its own expectations. Metrics move in the expected direction. Decisions justify previous decisions. The system experiences coherence, but forgets it’s not in contact with reality.

The most beautiful takeaway: **The brain is built to function this way.**

From the inside, coherence and correctness feel the same.

We experience truth as the absence of internal friction, as reality behaving the way we expect it to. But if our expectations were never aligned with the true objective in the first place, then in the absence of corrective feedback, coherence becomes indistinguishable from correctness.

What emerges is not irrationality, and whether a belief survives or collapses depends not only on its correctness, but on how much prediction error it generates under available feedback. 

In the absolute dark, coherence is not a failure mode. **It is the default mode.**




