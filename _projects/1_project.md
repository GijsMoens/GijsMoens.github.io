---
layout: page
title: A Foundational Model for Tennis Players
description: A personal project with ambition.
img: assets/img/alca.jpg
importance: 1
category: fun
related_publications: true
---


<h1 style="color:orange">UNDER CONSTRUCTION</h1>.
## Introduction

Despite the framing, this project is not fundamentally about tennis. Tennis merely serves as a constrained and well-structured domain in which a broader modeling problem can and might be studied.

Since I began learning about machine learning, I have been interested in constructing probabilistic models capable of predicting the outcomes of sporting events. Tennis is particularly appealing for this purpose: each match consists of exactly two players, and the outcome is binary (win/loss). This removes many confounding factors present in team sports, such as coordinated defensive strategies or role specialization, and yields a comparatively clean signal for predictive modeling.

In 2021, I began scraping historical ATP and WTA match data, collecting information on match outcomes, players, surfaces, and scores. This effort resulted in a continuously maintained database of professional tennis matches. While the infrastructure for data collection and storage has been in place for several years, the present work represents the first serious attempt to define a principled modeling framework on top of this data.

## The Data

The dataset is broad and relational in nature. It consists of tables describing players, matches, tournaments, surfaces, and point-level statistics where available. A schematic overview of the main tables and their relationships can be found here:

https://drive.google.com/file/d/1aamYIVzfs2M9Gm92gTR7F2mX0lh5fWQ_/view?usp=sharing

The structure allows matches to be analyzed both at an aggregate level (match outcome) and at finer temporal resolutions (sets, games, points).

## Philosophy

My grandmother is 93 years old and consistently predicts the winners of tennis matches with striking accuracy. This is not the result of randomness, nor of access to betting odds or statistical models, but rather of decades of exposure to the game. She has developed an intuition that appears to capture structure not explicitly encoded in standard metrics.

While this intuition is difficult to formalize or validate statistically, it strongly suggests the existence of latent variables governing match outcomes. In particular, tennis appears to involve a significant mental component that is not fully reflected in surface-level statistics.

As Roger Federer once remarked:

> “Even top ranked tennis players win barely more than half the points they play.”

Match outcomes are therefore often determined by a small subset of critical points. Performance under pressure like break points, set points, match points plays a disproportionate role. These effects are inherently difficult to quantify, but they motivate the search for models capable of capturing latent, time-varying player states.

## The Model

The objective is to construct a stochastic, event-independent, spatiotemporal model that captures both:

1. The evolution of a player’s latent skill and mental state over time.
2. The relational structure induced by matches played between players.

Conceptually, the model is a dynamic graph with feedback: information propagates forward in time, but relative skill comparisons induce indirect constraints across players. 

This formulation implicitly assumes that player skill lies on a low-dimensional manifold. While this assumption is likely violated, in practice players have heterogeneous strengths and weaknesses, it provides a tractable starting point.

The model decomposes naturally into two components:

- **Time**: the evolution of an individual player’s latent state.
- **Space**: the graph structure induced by interactions between players.

## Time

Time is treated at the finest meaningful resolution: the point. Although tournaments span days or weeks, the mental and performance-related state of a player can change from point to point. Consequently, match-level outcomes are viewed as aggregates of many latent state transitions.

Let the hidden latent state of a player at time \( t \) be denoted by

$$
H_t \in \mathbb{R}^d
$$

and let the observable or partially observable skill state be denoted by

$$
S_t
$$

The temporal dynamics are modeled as a linear stochastic state-space system:

$$
H_{t+1} = A H_t + B u_t
$$

$$
S_{t+1} = C H_t + D S_t
$$

Here, $$ u_t $$ represents an embedding of point-level events, such as:

- Serve indicator  
- Point outcome (win/loss)  
- Break point-, Set point- Match point status $$\in \{-1, 0, 1\} $$  

Each point induces a transition in the latent state, allowing the model to learn how pressure situations and momentum affect future performance. A match is therefore represented as a sequence of state updates rather than a single atomic event.

## Space

The spatial component of the model is defined through a dynamic interaction graph

$$
G_t = (V, E_t)
$$

where:

- $$ V $$ is the fixed (want to go to dynamical) set of players.
- $$ E_t \subset V \times V $$ is the set of directed, time-indexed edges corresponding to matches played up to time $$ t $$.

An edge

$$
(i \rightarrow j, t) \in E_t
$$

represents a match at time $$ t $$ in which player $$ i $$ plays player $$ j $$. 


