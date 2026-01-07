---
layout: post
title: Expertise Is Not Optional
date: 2025-03-02 14:24:00
description: When power is high and expertise is low, learning by doing stops being learning. It becomes gambling.
tags: learning experience judgment power understanding
categories: Weekly-Thoughts Non-Technical
---

**Proof-read by mam, so you've got this!!!**

This article is about learning as a prerequisite for doing, and how the cost of mistakes changes once the systems we interact with become powerful enough to actually hurt us back.

This is not the usual “experts vs. LLMs” debate, nor another AI bias rant (we’ve mostly lost that one already, folks). Think of this instead as my own attempt to formalize an intuition I keep tripping over, and honestly a reminder to myself of why expertise quietly stops being optional once leverage enters the picture.

---

## Two ways to learn

As far as I can tell from my own experience, there are only two fundamental ways humans learn.

### 1. Learning by observing (indirect learning)

A child doesn’t need to insult someone to learn that it hurts. Watching how others react, tone changing, faces tightening, silence falling, is often enough to build a model.

This is learning by observing. No direct action is required, just attention. Watching the world, extracting patterns, forming internal models.

It’s how we learn to understand social norms, learn from books, and survive school. It’s also why explanations exist, and why we ask friends or parents for advice, which we then confidently ignore.

---

### 2. Learning by doing (direct learning)

Then there’s the other way: learning by doing.

- You fall off the bike.  
- You burn the food.  
- You send the message you absolutely shouldn’t have sent.

This kind of learning is slow, frustrating, and expensive.

But it’s also deep. It’s how we build intuition and judgment.  It’s why experience exists.

Both modes are essential, but they are **not interchangeable**.

Learning by observing is cheap.  
Learning by doing is costly.

---

Let’s formalize this just enough to make that distinction precise. From here on, I want to formalize my intuition. It may look complex, but it really isn’t.

---

## Formal setup

Let:
- $$S$$ be any system you’re interacting with  
  (a car, a company, a relationship).
- $$u \in U$$ be an action you can take  
  (steer left, fire an employee, bring up *that* argument).
- $$E$$ be your level of expertise with the system  
  (capabilities, experience, intuition).
- $$P$$ be the power of the system  
  (speed, impact, irreversibility, emotional leverage).
- $$C(u; P, E)$$ be the cost of taking action $$u$$  
  (hitting an *Amsterdammertje*, losing trust, turning a minor disagreement into a multi day discussion).
- $$K(u)$$ be the knowledge gained from that action  
  (how to drive, manage people, communicate).

The key point is that **cost is not intrinsic to the action alone**.  
It depends on both the **power of the system** and your **expertise**.

---

## Axiom 1: Learning can introduce costs

Learning by doing means accepting:

$$
C(u; P, E) > 0 \quad \text{in exchange for} \quad K(u)
$$

We pay for learning.

Learning by observing means:

$$
C(u; P, E) \approx 0 \quad \text{while still gaining} \quad K(u)
$$

We gain knowledge without paying for it.

---

## Axiom 2: Learning by doing requires bounded cost

For learning by doing to be safe, we need:

$$
\sup_{u \in U} C(u; P, E) < \infty
$$

In words, the upper bound on cost must be finite and acceptable. We only live once (I hope), and we can’t afford catastrophic mistakes.

This is why:
- pilots train in simulators,
- companies run small experiments,
- people sometimes think before they speak.

---

## Axiom 3: System power scales the cost of mistakes

Recall that $$P$$ denotes the power of a system.

Then:

$$
\mathbb{E}[C(u; P, E)] \propto P
$$

The cost of mistakes scales with power.

- A mistake in a notebook costs minutes.  
- A mistake towards clients can cost days.  
- A mistake in cars can cost lives.

---

## Axiom 4: Expertise reduces the cost of mistakes

Let $$E$$ denote expertise.

Then:

$$
\mathbb{E}[C(u; P, E)] \propto \frac{P}{E}
$$

Expertise doesn’t eliminate mistakes. It **shrinks their expected cost**, on average action $$u$$ under system power $$P$$ and expertise $$E$$ leads to lower costs.

- It’s seeing further ahead on the road.  
- It’s managing resources inside a company.  
- It’s knowing when to drop an argument.


---

## Proposition: Learning by doing becomes unsafe when power outpaces expertise

If $$P$$ grows faster than $$E$$, then:

$$
\sup_{u \in U} C(u; P, E) \to \infty
$$

The costs explodes. A child can absolutely learn to drive by doing. Given enough time and feedback, the learning signal is there.

But the system has:
- high power,
- low expertise.

The issue isn’t the ability to learn. The issue is **cost of error overwhelming expertise**.

---

## Theorem: Safe learning requires either low power or high expertise

Let us call an action $$u$$ *safe* under system power $$P$$ and expertise $$E$$ if its expected cost stays below some tolerance $$\epsilon > 0$$:

$$
\mathbb{E}[C(u; P, E)] \leq \epsilon
$$

In words, safe learning means acting and learning from acting at a cost we are willing to pay.

This condition can only be satisfied in one of two ways:

$$
(P \text{ is small}) \ \lor \ (E \text{ is large})
$$

Meaning that either we are dealing with:

### 1. Low system power $$P$$  
Mistakes are cheap, reversible, and contained.

- Taking a car for a spin in an empty parking lot  
- Rearranging desks at the office  
- Saying the wrong thing among forgiving people  

### 2. High expertise $$E$$  
Mistakes are anticipated, mitigated, or avoided.

- Driving lessons with an instructor  
- Mentorship at work  
- Knowing when to drop an argument  

There is no third option.

**When power is high and expertise is low, learning by doing stops being learning. It becomes gambling.**

---

## Why this matters now

Modern tools, especially AI, massively increase $$P$$. Expertise $$E$$ does **not** scale automatically.

The mistake isn’t learning by doing, or using powerful tools to save time.  
The mistake is allowing $$P$$ to grow faster than $$E$$.

Or put differently:

> Learning by doing is great, as long as the thing you’re steering can afford your ignorance.

Not because experimentation is bad, but because **power and expertise must scale together**.

---

## Corollary: Observation precedes action in high-power systems

When system power $$P$$ is large and expertise $$E$$ is still low, learning by doing can’t be the default. The only viable option is to **learn by observing first**.

In practice, this means:
1. read into the complex material,
2. reason about consequences before touching the real system,
3. simulate actions where failure is cheap,
4. *then* act carefully.

Observation is not a lack of initiative. Wanting to build the startup, send the email, or push the money printing idea is understandable. It’s just a bad idea to do so without knowing what you’re doing.

Observation is how expertise is built without externalizing the cost of ignorance. Not as gatekeeping, but as the minimum respect owed to systems powerful enough to punish carelessness.

