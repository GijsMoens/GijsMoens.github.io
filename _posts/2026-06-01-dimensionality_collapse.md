---
layout: post
title: "Polarisation as Dimensionality Collapse"
date: 2026-06-01 10:00:00
description: Polarisation is not disagreement. It is what happens when high-dimensional human beings are compressed into low-dimensional symbolic systems and then judged as if the projection were the person.
tags: polarisation dimensionality-reduction systems-thinking philosophy machine-learning
categories: Weekly-Thoughts Non-Technical
---

I keep bumping into the same bad explanation for polarisation. It goes: people are becoming more extreme, more tribal, less empathetic. Echo chambers. No one listens anymore. If only we'd be kinder.

It's not wrong, exactly. It's just boring. Diagnosing symptoms while sounding profound. The rhetorical equivalent of diagnosing a fever by noting that the patient feels warm.

Here's what I actually think is going on. Polarisation isn't a failure of empathy, civility, or rationality. It's a failure of **dimensionality**. It's what happens when high-dimensional human beings, with many partially independent beliefs, histories, identities, incentives, wounds, loyalties, and contradictions, get compressed into low-dimensional symbolic systems and then judged as if the projection were the person.

The curse of dimensionality has a social analogue that we've barely begun to take seriously.

Polarisation is **dimensionality collapse**.

---

## People are high-dimensional

Think of an actual person. Not a demographic profile or a Twitter bio. A real one.

This person holds views on economic policy shaped by growing up in a household where money was unstable. They've got a complicated relationship with institutional religion: drawn to the aesthetics and the community, alienated by the doctrine, privately furious about the politics, but they still go at Christmas and aren't entirely sure why. They distrust pharmaceutical companies but vaccinate their children. They vote for a party whose cultural positions they find embarrassing but whose economic instincts roughly match their own, which they find embarrassing in a different way. They were radicalised briefly in their twenties by a book they now find simplistic but still quote at dinner parties. They think modern art is mostly a money-laundering operation but cried at a Rothko once and have never told anyone.

They hold contradictions they've never resolved and don't experience as contradictions, because they live in all their dimensions simultaneously. Which is what living is.

This person isn't a point on a line. They're a point in a space of enormous dimension.

Formally:

$$x \in \mathbb{R}^n$$

where $$n$$ is large and each coordinate encodes something partially independent: an economic preference, a cultural affiliation, a class memory, an aesthetic sensibility, a religious impulse, a trauma response, a tolerance for risk, a theory of human nature, an opinion on whether a hot dog is a sandwich.

These dimensions aren't neatly orthogonal, but they're not reducible to one another either. Someone's position on immigration doesn't fully determine their position on monetary policy, which doesn't fully determine their relationship to tradition, which tells you nothing whatsoever about whether they think the moon landing was faked.

The human being isn't just quantitatively complex. It's **ontologically heterogeneous**: material, symbolic, historical, affective, economic, religious, familial, institutional, existential dimensions coexisting within a single subject. No common metric.

And here's the problem. Society, in order to function at scale, has to make people **legible**. Legibility costs dimensions.

---

## Everything compresses you

Every political system, every media ecosystem, every bureaucratic apparatus does the same thing to a human being: makes them smaller.

Left or right. Progressive or conservative. Woke or anti-woke. Elite or people. Us or them. Pick one. You've got five seconds.

This is a compression function:

$$f: \mathbb{R}^n \rightarrow \mathbb{R}^k, \quad k \ll n$$

The output $$f(x)$$ is a political identity, a media profile, a demographic segment, a moral category. It keeps some information about the original vector $$x$$ and throws away most of it. The compression is **lossy**. The question is never whether information is lost, but which information, and whether anyone notices.

In the simplest case, $$k = 1$$. The whole person, projected onto a single axis:

$$z = w^\top x$$

A scalar. A score. A position on a line.

The person who's fiscally conservative but socially liberal, culturally traditional but institutionally sceptical, who listens to both country music and NPR and sees no tension in this: they don't survive the projection. They become a point on a line, and the line doesn't have room for them.

Now here's where the curse of dimensionality kicks in. When you compress a high-dimensional space into a low-dimensional one, you wreck distances. Two people who are genuinely close in the original space, who share values, experiences, temperaments, who'd get along great, can end up looking like enemies because they differ on one or two dimensions that happen to be heavily weighted in the current projection. Maybe one uses the language of social justice and the other doesn't. Maybe one says "inequality" and the other says "unfairness" and neither recognises the other's dialect.

$$d(x_i, x_j) \text{ is small}$$

$$d(f(x_i), f(x_j)) \text{ is large}$$

And the reverse happens too. People who share almost nothing, different values, different theories of the good, different ideas about what constitutes a reasonable bedtime, end up projected onto the same point because they use the same vocabulary or post the same memes.

Artificial proximities. Artificial oppositions. Alliances manufactured from coincidence and enemies manufactured from dialect.

Polarisation isn't people becoming more different. It's people **appearing** more different because the space they're represented in has collapsed.

---

## The weird bundling problem

One of the strangest signatures of polarisation, once you see it, is the progressive correlation of dimensions that have no business being correlated.

In any healthy epistemic ecosystem, someone's position on tax policy should be largely independent of their position on vaccine mandates, which should be largely independent of their aesthetic preferences, which should be largely independent of their theory of gender, which should be largely independent of their feelings about cryptocurrency, which should be largely independent of their opinion on whether it's acceptable to recline your seat on a short-haul flight.

But under polarisation:

$$\text{corr}(x_a, x_b) \rightarrow 1$$

If you know someone's position on climate policy, you can predict with disturbing accuracy their position on gun control, their feelings about academia, their dietary preferences, their opinion of a specific comedian, whether they own a pickup truck, and which streaming service they consider morally superior. Tell me your view on pronouns and I'll tell you your view on central banking. This should be bizarre. It's treated as natural.

It's not because these things are logically connected. The compression function has **forced** them onto the same axis. The projection $$f$$ maps independent dimensions onto a single coordinate, creating a phantom correlation structure that doesn't exist in the underlying reality. The political equivalent of seeing a face in a cloud, except the face is wearing a red hat or a rainbow pin and everyone's arguing about its expression.

If you've done PCA with too few components, you know the artefact. Spurious correlations between variables that are independent in the original space. The representation looks structured, but the structure is an artefact of the compression, not a feature of the data.

Polarisation does this to people. Takes the uncorrelated mess of actual human opinion and irons it into bundles. Then treats the bundles as ideologies, as if the bundling were a discovery rather than an imposition.

---

## Ideology is just a compression algorithm

An ideology isn't primarily a set of beliefs. It's a **compression algorithm**. A function that takes the irreducible complexity of human experience and maps it onto one, maybe two dimensions. That's the most a slogan can hold.

The left-right axis is a principal component. Captures the largest single direction of variance in political opinion, collapses everything else. Most of the person ends up in the residual. The residual doesn't get a vote.

What makes ideology powerful isn't its accuracy but its **compression ratio**. An $$n$$-dimensional object rendered in $$k$$ dimensions, where $$k$$ is small enough for a headline, a hashtag, or a campaign button.

And look, compression is necessary. We can't navigate eight billion $$n$$-dimensional beings without some form of reduction. The question isn't whether to compress, it's whether we remember that we're compressing.

The ideologue isn't someone who simplifies. Everyone simplifies. The person who claims to reject ideology is just running an unlabelled compression function and calling the output "common sense." The ideologue is someone who's **forgotten that they're simplifying**. They've mistaken the map for the territory. The coordinate for the character.

---

## Extremes are attractors

When you collapse a high-dimensional space onto a single axis, the endpoints become the most legible positions available. They're the positions the compression function represents most faithfully, because they require the least information: you are maximally one thing. The centre is a region of high ambiguity, countless different positions in the original space all mapped to the same indistinct middle. The moderate isn't moderate because they lack conviction. They're illegible because the representational system lacks the bandwidth for what they actually think.

So people drift toward the extremes, not because they become more extreme in their actual views, but because the system rewards extremity with **legibility**. To be moderate in a polarised system is to be perpetually misread. To be extreme is to be instantly classifiable. To be classifiable is to belong. And belonging, for a social species, might be the incentive.

Here's the feedback loop. The system classifies people. People, wanting legibility and belonging, start conforming to the classification. The map shapes the territory. Categories that were imposed become identities that are inhabited. People start saying things they half-believe because the things they fully believe don't fit on the axis. Eventually they forget which beliefs were original and which were adopted for legibility.

The compression becomes the person.

---

## Pointing from inside the projection

This is the part I find most uncomfortable, and I'm writing it knowing full well that I do this too.

The most destructive feature of polarisation isn't disagreement. It's that people **point at others from inside a reduced coordinate system without realising they're performing dimensionality reduction**.

They observe one coordinate, a vote, a bumper sticker, a dietary choice, a social media post made at 11pm after two glasses of wine, and infer the whole vector. They see a point on a line and mistake it for a soul.

"I know what kind of person you are" almost always means "I know where my model places you." It's a statement about the speaker's compression function, not about the other person. But it feels like direct perception. The model is invisible to the person using it.

This is how polarisation produces cruelty while feeling righteous. Within the compressed representation, the judgement is consistent. You see someone at a specific point on your axis and respond with the moral weight you think that point deserves. But the point isn't the person. The person has been collapsed, and the collapsed version is being punished for crimes that belong to the projection.

A person contains contradictions that coexist peacefully across multiple dimensions. The compressed version reads these as hypocrisy, because in one dimension, holding two positions means occupying two points on the same line, which looks like dishonesty. In the original space, those positions may not be on the same axis at all. They may be as unrelated as a preference for sourdough and a theory of property rights.

When you can only see one axis, the world looks extraordinarily clear. Good and evil along a line. Everyone has a location. The clarity is real, but it's the clarity of a shadow on a wall: sharp, definite, missing a dimension. Plato understood this. He also understood that the people watching the shadows wouldn't thank you for pointing out the fire.

And here's the thing I keep having to remind myself: the temptation to imagine that *I* see the full dimensionality while others are trapped in their projections? That's itself a compression. The moment you reduce someone to a point on your axis, you've accepted the axis. You've agreed to play in $$\mathbb{R}^k$$. You're now also $$k$$-dimensional. Congratulations.

Both sides accuse each other from inside different projections of the same higher-dimensional object. They're not looking at the same thing and disagreeing. They're looking at different shadows and arguing about which shadow is real. You can't point that out from inside either shadow without sounding like you're defending the other one.

And eventually, under sustained polarisation, the missing dimensions don't even appear as missing. They just don't appear. You can't show someone a dimension they don't have. You're trying to point up in a world that only has left and right.

---

The cure for polarisation isn't the abolition of disagreement. Disagreement is high-dimensional; it needs the full space to express itself faithfully. The cure is the recovery of lost dimensions.

A society is healthy not when everyone agrees, but when no single axis is allowed to exhaust the human.
