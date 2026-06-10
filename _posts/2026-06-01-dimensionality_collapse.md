---
layout: post
title: "Polarisation as Dimensionality Collapse"
date: 2026-06-01 10:00:00
description: Polarisation is what happens when high-dimensional people get compressed into low-dimensional categories and then judged as if the category were the person.
tags: polarisation dimensionality-reduction systems-thinking philosophy machine-learning
categories: Weekly-Thoughts Non-Technical
---

There's a standard explanation for polarisation that I keep running into: people are becoming more extreme, more tribal, less empathetic. Echo chambers. No one listens. If only we'd be kinder.

I don't think that's what's happening. Or rather, I think it's describing symptoms of something more structural.

My claim is that polarisation is a failure of **dimensionality**. It's what happens when high-dimensional human beings get compressed into low-dimensional categories and then treated as if the compressed version were the real one. If you've ever dealt with the curse of dimensionality in machine learning, the social version of it is surprisingly recognisable.

---

## People are high-dimensional

Think of someone you know well. Not their political label. The actual person.

They probably hold economic views shaped by their family situation growing up. They've got some complicated relationship with religion or the lack of it. They might distrust large institutions but still rely on them. They vote for a party they're not fully comfortable with. They hold views that technically contradict each other but have never felt the need to reconcile them because those views live in completely different parts of their life.

That person isn't a point on a line. They're a point in a high-dimensional space.

$$x \in \mathbb{R}^n$$

where $$n$$ is large and each coordinate captures something partially independent: economic preferences, cultural affiliations, class background, aesthetic sensibilities, risk tolerance, relationship to authority, and so on. These dimensions aren't perfectly orthogonal, but they're not reducible to each other either. Knowing someone's view on immigration tells you surprisingly little about their view on monetary policy, which tells you little about their relationship to tradition.

The key thing here is that people aren't just complicated in a quantitative sense. The dimensions are **ontologically different** from each other: material, symbolic, historical, emotional, economic, religious, familial. They don't share a common scale. You can't meaningfully average someone's trauma response with their tax preferences.

But society needs to make people legible in order to function at scale. And legibility costs dimensions.

---

## Everything compresses you

Every political system, media platform, and bureaucratic process takes this high-dimensional person and compresses them.

Left or right. Progressive or conservative. Woke or anti-woke. Us or them.

Formally, that's a compression function:

$$f: \mathbb{R}^n \rightarrow \mathbb{R}^k, \quad k \ll n$$

The output $$f(x)$$ is a political identity, a demographic segment, a moral category. It keeps some information about the original vector and discards most of it. The compression is lossy by definition. The question isn't whether information is lost, it's which information, and whether anyone remembers that it was.

In the most extreme case, $$k = 1$$. The whole person projected onto a single axis:

$$z = w^\top x$$

The result is a scalar, a position on a number line from left to right.

Now here's where the curse of dimensionality shows up. When you compress a high-dimensional space into a low-dimensional one, you distort distances. Two people who are close in the original space (similar values, similar experiences, would get along fine) can end up looking like enemies because they differ on one or two dimensions that happen to be heavily weighted in the current projection. Maybe one uses progressive language and the other doesn't. Maybe they have the same concern about inequality but express it differently.

$$d(x_i, x_j) \text{ is small}$$

$$d(f(x_i), f(x_j)) \text{ is large}$$

And the reverse: people who share almost nothing can end up projected onto the same point because they use the same vocabulary or belong to the same party.

This is projection error. It's the mathematically inevitable consequence of dimensionality reduction. You create artificial proximities and artificial oppositions.

Polarisation isn't people becoming more different. It's people **appearing** more different because the representational space has collapsed.

---

## The bundling problem

One of the more interesting signatures of polarisation is the increasing correlation between dimensions that have no logical reason to be correlated.

Someone's position on tax policy should be largely independent of their position on vaccine mandates, which should be largely independent of their aesthetic preferences, which should be largely independent of their theory of gender, which should be largely independent of their feelings about cryptocurrency.

Under polarisation, these correlations increase:

$$\text{corr}(x_a, x_b) \rightarrow 1$$

If you know someone's climate position, you can predict their gun control position, their dietary habits, their feelings about academia, and probably which podcasts they listen to. Tell me your view on pronouns and I'll tell you your view on central banking. None of these are logically connected, but the compression function has forced them onto the same axis.

If you've done PCA with too few components, you've seen this artefact. You get spurious correlations between variables that are independent in the original space because the components mix signals that should stay separate. The resulting structure looks real but it's an artefact of the compression.

Polarisation does this to people. It takes the uncorrelated mess of actual human opinion and forces it into bundles. Then it treats the bundles as ideologies, as if the bundling were a discovery rather than something we imposed.

---

## Ideology as compression

An ideology, in this framing, isn't primarily a set of beliefs. It's a **compression algorithm**. It takes the complexity of human experience and maps it onto one, maybe two dimensions.

The left-right axis is basically a principal component. It captures the largest direction of variance in political opinion but collapses everything else. Most of what makes a person who they are ends up in the residual, and the residual doesn't get represented.

Compression is necessary, obviously. You can't reason about eight billion people without some form of reduction. The issue isn't that we compress, it's whether we remember that we're doing it.

Everyone simplifies. The person who claims to reject ideology is just running an unlabelled compression function and calling the output "common sense." The problem starts when you forget you're simplifying. When the compressed representation starts looking like the territory instead of a lossy map of it.

---

## Extremes as attractors

When you collapse a high-dimensional space onto a single axis, the endpoints become the most legible positions. They require the least information to represent: you are maximally one thing. The centre is ambiguous because countless different positions in the original space all map to the same middle region.

So people get pulled toward the extremes, not because their actual views become more extreme, but because the system rewards extremity with legibility. Being moderate in a polarised system means being perpetually misread. Being extreme means being instantly classifiable, and being classifiable means belonging.

There's a feedback loop here that I think is underappreciated. The system classifies people. People want to be legible, so they start conforming to the classification. Categories that were imposed become identities that are inhabited. People start holding positions they only half-believe because the positions they actually hold don't fit neatly on the axis. After a while, it gets hard to tell which beliefs were original and which were adopted for legibility.

---

## Pointing from inside the projection

This is the part I find hardest to write about honestly, because I do this too.

The most damaging thing about polarisation isn't that people disagree. It's that people judge others from inside a compressed representation without realising they're working with a compressed representation.

You see someone's vote, or their opinion on one topic, and you fill in the rest of the vector. "I know what kind of person you are" really means "I know where my model places you." It's a statement about your own compression function, not about the other person. But it doesn't feel that way. It feels like you're just seeing clearly.

This is how polarisation produces harsh judgements that feel completely justified. Within the compressed space, the judgement is consistent. You see someone at a point on your axis and respond to that point. But the point isn't the person. The person got collapsed into it, and the collapsed version is being held accountable for things that belong to the projection.

A real person contains contradictions that coexist across different dimensions. In a one-dimensional representation, those contradictions look like hypocrisy, because holding two positions on the same line looks like dishonesty. In the original space those positions might not be on the same axis at all.

And the uncomfortable part: thinking that *you're* the one who sees the full picture while others are stuck in their projections? That's also a compression. The moment you reduce someone to a position on your axis, you've accepted the axis. You're now operating in the same low-dimensional space.

Both sides of most polarised debates are pointing at each other from inside different projections of the same higher-dimensional reality. They're not disagreeing about the same thing. They're each looking at a different low-dimensional slice and arguing about which slice is the real one.

Under sustained polarisation, the missing dimensions don't even register as missing. They just aren't there. And you can't point someone toward a dimension that doesn't exist in their coordinate system.

---

The cure for polarisation isn't getting everyone to agree. Disagreement is high-dimensional and needs the full space to express itself properly. The cure is recovering the dimensions we've lost.

A society is healthy not when everyone agrees, but when no single axis gets to define what a person is.
