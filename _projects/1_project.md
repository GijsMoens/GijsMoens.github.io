---
layout: page
title: A Foundation Model for Tennis Players
description: A spatiotemporal equilibrium approach to latent performance modeling.
img: assets/img/alca.jpg
importance: 1
category: fun
related_publications: true
---

## Introduction

Despite the framing, this project is not fundamentally about tennis.

Since I began learning about machine learning, I have been interested in constructing probabilistic models capable of predicting the outcomes of sporting events. Tennis is particularly appealing for this purpose: each match consists of exactly two players, and the outcome is binary (win/loss). This removes many confounding factors present in team sports—such as coordinated defensive strategies or role specialization—and yields a comparatively clean signal for predictive modeling.

In 2021, I began scraping historical ATP and WTA match data, collecting information on match outcomes, players, surfaces, tournaments, and scores. This effort resulted in a continuously maintained database of professional tennis matches. While the infrastructure for data collection and storage has been in place for several years, the present work represents the first serious attempt to define a principled modeling framework on top of this data.

The ambition of this project is not merely to predict match outcomes, but to construct a *foundational representation* of players: a latent, time-varying model of skill and mental state that evolves through competition.

---

## Philosophy

My grandmother is 93 years old and consistently predicts the winners of tennis matches with striking accuracy. This is not the result of randomness, nor of access to betting odds or statistical models, but rather of decades of exposure to the game. She has developed an intuition that appears to capture structure not explicitly encoded in standard metrics. A kind of probablistic view of potential trajectories of a latent space encoding a players state and how they interact. **wink, wink**.

While this intuition is difficult to formalize or validate statistically, it strongly suggests the existence of latent variables governing match outcomes. In particular, tennis appears to involve a significant mental component—performance under pressure, momentum, resilience—that is not fully reflected in surface-level statistics.

As Roger Federer once remarked:

> “Even top ranked tennis players win barely more than half the points they play.”

Match outcomes often come down to a handful of critical points. Break points, set points, match points, etc. Those moments just feel different, and how a player performs under that kind of pressure can completely swing a match. It’s hard to put numbers on this, but it’s one of the main reasons I’m interested in models that can capture latent, time-varying player states.

A lot of existing models implicitly treat every point the same, using fixed, time-invariant weights. In that world, losing a break point is no different from losing a point at 15–30. That might be mathematically convenient, but it doesn’t really line up with how tennis, or sport in general, actually worksI think.

My intuition is that pressure isn’t caused by a single point in isolation. It builds up. It’s the combination of multiple points, the missed chances, the small momentum shifts, that start to matter. Those sequences can change a player’s confidence, decision-making, and execution in ways that don’t immediately reset on the next point. If that intuition is even partially right, then we need models that let state evolve with context and recent history, rather than assuming every point is felt the same.

---

## The Data

The dataset is broad and relational in nature. It consists of tables describing players, matches, tournaments, surfaces, and where available—point-level statistics.

The structure allows matches to be analyzed at multiple temporal resolutions:

- Match-level outcomes (win/loss)
- Set- and game-level progression
- Point-by-point sequences (serve status, score state, break points)

This multi-scale structure motivates a modeling approach in which time is treated as a continuous process rather than a sequence of isolated events.

The full database diagram can be found here:

[Database Diagram](https://drive.google.com/file/d/1aamYIVzfs2M9Gm92gTR7F2mX0lh5fWQ_/view?usp=sharing)

The database is hosted on a PostgreSQL server and filled with data scraped from various sources. Every night, new matches are added to the database and the data is kept up to date. 

---

## Modeling Objective

The objective is to construct a stochastic, event-driven, spatiotemporal model that captures both:

1. The evolution of an individual player’s latent skill and state **within a match** as points unfold.
2. The evolution of the **global population** of player representations **between matches**, as a function of match dynamics.

Conceptually, the model is a dynamic graph with feedback. Within a match, players move through a trajectory in latent space driven by point outcomes and score context. After the match ends, the information contained in that trajectory is distilled into a force (or constraint) that updates the entire player network.

The key insight is to model these two processes separately:

- **Intra-match dynamics (micro)**: high-frequency latent evolution driven by points.
- **Inter-match dynamics (macro)**: low-frequency, global equilibrium update driven by full match iteractions.

Matches are not treated as atomic events; they are treated as *time series* whose internal structure determines how the world-model changes.

---

## Latent State Representation

Each player $$i$$ has a latent representation that exists at two timescales:

- A **global state** evaluated only at match basis.
- A **match state** that evolves point-by-point during an ongoing match.

We define the *global* player state at match index $$m$$ as:

$$
z_i^{(g)}(m) \in \mathbb{R}^d
$$

This vector is meant to capture stable, slowly varying aspects of performance: skill, long-term form, and longer-horizon mental components.

When player $$i$$ participates in match $$m$$, we initialize an *intra-match* state:

$$
z_{i,m}^{(p)}(0) = z_i^{(g)}(m)
$$

and then evolve it point-by-point throughout the match.

---

## Process 1: Intra-Match Evolution 

Consider a match $$m$$ between players $$i$$ and $$j$$, consisting of points indexed by $$t = 0,1,\dots,T_m-1$$.

Let $$u_m(t)$$ be a feature vector encoding the context of point $$t$$. We evolve each player’s intra-match state with a stochastic transition:

$$
z_{i,m}^{(p)}(t+1) = f_\theta\!\left(z_{i,m}^{(p)}(t), \; z_{j,m}^{(p)}(t), \; u_m(t)\right) + \epsilon_{i,t}
$$

$$
z_{j,m}^{(p)}(t+1) = f_\theta\!\left(z_{j,m}^{(p)}(t), \; z_{i,m}^{(p)}(t), \; u_m(t)\right) + \epsilon_{j,t}
$$

with noise:

$$
\epsilon_{i,t}, \epsilon_{j,t} \sim \mathcal{N}(0, Q)
$$

Notes:

- $$f_\theta$$ will probably be linear (SSM based approach).
- The dependency on the opponent state allows momentum/pressure to be relational rather than purely individual.

What we obtain is a latent trajectory for each player during the match:

$$
\{z_{i,m}^{(p)}(t)\}_{t=0}^{T_m}, \quad \{z_{j,m}^{(p)}(t)\}_{t=0}^{T_m}
$$


This defines a discrete-time vector field on the match-level state space, governing momentum, pressure response, collapse, and recovery. We can tie the latent states directly to observables by defining the probability that player $$i$$ wins point $$t$$ as:

$$
p_t
:=
p(\text{point}_t = i \mid z_{i,m}^{(p)}(t), z_{j,m}^{(p)}(t), u_m(t))
=
\sigma\!\left( g_\phi(u_m(t), z_{i,m}^{(p)}(t), z_{j,m}^{(p)}(t)) \right).
$$

Now, The the game-win probability and match outcome emerges from the sequence of point outcomes, but crucially: **the match produces an entire latent trajectory**, not just a final win/loss.

---

## Compressing Match Dynamics into a Match Summary

After the final point, each player has a terminal intra-match state:

$$
z_{i,m}^{(p)}(T_m), \quad z_{j,m}^{(p)}(T_m),
\qquad
\text{with } z_{i,m}^{(p)}(t)\in\mathbb{R}^{D_p}.
$$

To compare global and intra-match states, we map the global state into the intra-match space: $$\mathbb{R}^{D_g}\to\mathbb{R}^{D_p}$$. We then compress the match into a summary object $$r_m$$ that will drive the global update:

$$
r_m
=
\mathrm{Enc}_\psi\!\left(
z_{i,m}^{(p)}(T_m) - z_{i,m}^{(p)}(0),\;\;
z_{j,m}^{(p)}(T_m) - z_{j,m}^{(p)}(0)
\right).
$$

This object $$r_m$$ acts as the bridge: it distills the match outcome in latent space into a signal used to update the global player graph. We purposefully avoid using $$z_{i,m}^{(p)}(T_m)$$ as the new player representation directly, since that would conflate intra-match dynamics with global skill, on some days our true skills and the way we perform in a match can diverge quite a lot. We could therefore day that $$r_m$$ captures the *performance $$\Delta$$* during the match relative to the starting point.

---

## Process 2: Inter-Match Global Update

At this point, I like to think of each completed match \(m\) as an interaction edge in a graph over players. The mental picture that works best for me is a spring system: every player has a position in some latent space, and every match applies a force that pulls or pushes those positions based on both the result and how the match actually played out.

In this view, a match doesn’t just update the two players who were on court. Because everyone is connected through a web of past interactions, changing one edge slightly reshapes the whole configuration. A force applied in one place propagates through the network, nudging the relative positions of other players as well. This feels much closer to how tennis works in reality, where results indirectly affect how we perceive many players, not just the ones involved.

Thinking about the system this way also suggests that each time step can be treated independently. After all the forces induced by observed matches are applied, the network should settle into a new configuration. That configuration — the overall “tension” in the spring system — can be thought of as a snapshot of the current state of professional tennis. Instead of explicitly tracking long chains of historical updates, the latent positions themselves encode the accumulated effect of past interactions.

Formally, let the global interaction graph at match index $$m$$ be

$$
G_m = (V, E_{\le m}),
$$

where each completed match contributes an edge $$e_m = (i, j, m)$$ between the two players involved. As more matches are played, this graph gradually fills in, capturing who has played whom, under what conditions, and with what outcomes.

## Match-conditioned interaction energy

Each match introduces a constraint on where the two players involved should sit in latent space. Rather than basing this constraint only on win or loss, I let it depend on a richer summary of the match:

$$
E_m\!\left(z_i^{(g)}, z_j^{(g)}\right)
=
\mathcal{L}\!\left(
y_m,\;
z_i^{(g)}(m),\;
z_j^{(g)}(m),\;
r_m,\;
x_m
\right).
$$

Here, $$y_m$$ is the outcome, $$x_m$$ includes things like surface or tournament, and $$r_m$$ is meant to capture *how* the match unfolded — momentum swings, pressure moments, collapses, clutch play, and so on. Intuitively, this energy measures how reasonable the current global representations of the two players are given what we just observed on court.

From a probabilistic point of view, this energy is just the negative log-likelihood of the observed outcome,

$$
E_m = -\log p(y_m \mid \cdot),
$$

so a match that fits the current picture of the world applies only a small force, while a surprising or highly informative match applies a much stronger one.

## Global energy: springs with an anchor

Between matches, I assume that player representations shouldn’t move around too wildly. In the absence of strong new evidence, players should mostly stay where they are, aside from slow effects like rest, recovery, or gradual changes in form. I encode this with a simple prior evolution,

$$
\tilde z_i^{(g)}(m+1) = z_i^{(g)}(m) + \xi_{i,m},
$$

which gives a “default” next position for each player.

The full global objective after observing match $$m$$ then looks like this:

$$
E_{\le m}
=
\sum_{k \in E_{\le m}} \alpha_k \,
E_k\!\left(
z_{i(k)}^{(g)}(m+1),
z_{j(k)}^{(g)}(m+1)
\right)
+
\lambda \sum_{i \in V}
\left\|
z_i^{(g)}(m+1)
-
\tilde z_i^{(g)}(m+1)
\right\|^2.
$$

The first term collects the forces coming from all observed matches. Each one acts like a spring between two players, pulling them into relative positions that make sense given what happened. The weights $$\alpha_k$$ let older matches matter less over time, which matches the intuition that recent results are usually more informative.

The second term is there to keep things sane. It acts like inertia, or a soft tether tying each player to where we expected them to be. Without this anchor, the whole system could slide around or drift in latent space without changing any of the relative match constraints. The anchor makes sure that updates stay smooth and incremental, instead of redefining the entire landscape after every match.

Intuitively, this term prevents the model from overreacting. New matches can reshape the global configuration, but only as much as the evidence justifies. The result is a sequence of equilibrium states, each one representing a coherent snapshot of the competitive landscape at that point in time.
 
---

## Summary: Two coupled processes

The framework is intentionally split into two interacting components:

### 1) Intra-match (micro) dynamics

Within a match, latent player states evolve point by point in response to score context, serve status, pressure situations, and recent history. The output is not just a win or loss, but a full latent trajectory capturing momentum and mental state shifts.

### 2) Inter-match (macro) equilibrium

After the match ends, this trajectory is compressed into a summary signal $$r_m$$, which induces forces on the global player graph. The updated player embeddings are obtained by relaxing the entire system to a new equilibrium that reflects all observed interactions so far.

In this view, a match is not an atomic datapoint. It is a dynamical object whose internal structure determines how the global representation of the sport evolves.

---

## Outlook

This project is still very much in progress, both conceptually and technically. Beyond that, several open questions remain. How should the two processes be trained together? Possible approaches include alternating optimization, full end-to-end training with backpropagation through time, or a variational formulation in which latent trajectories are treated probabilistically. There are also practical issues around cold start and uncertainty: early in a player’s career, we should probably represent not just where they are in latent space, but how confident we are about that position.

Finally, there is the question of richer data. Ideally, the model would distinguish how points are won, winners versus unforced errors, forehands versus backhands, volleys versus baseline exchanges. That would require significantly more detailed data collection, but in principle, many of these distinctions could also emerge implicitly in the latent space if the point-level model is expressive enough. At least, that’s the hope.

