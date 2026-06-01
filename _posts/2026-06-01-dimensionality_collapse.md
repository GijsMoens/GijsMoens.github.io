---
layout: post
title: "Polarisation as Dimensionality Collapse"
date: 2026-06-01 10:00:00
description: Polarisation is not disagreement. It is what happens when high-dimensional human beings are compressed into low-dimensional symbolic systems and then judged as if the projection were the person.
tags: polarisation dimensionality-reduction systems-thinking philosophy machine-learning
categories: Weekly-Thoughts Non-Technical
---

There is a common story about polarisation. It goes something like this: people are becoming more extreme, more tribal, less empathetic. They retreat into echo chambers. They demonise the other side. They lose the ability to have reasonable conversations.

This story is not wrong, exactly. But it describes symptoms while misidentifying the disease.

What I want to argue is something more specific and, I think, more unsettling. Polarisation is not primarily a failure of empathy, civility, or rationality. It is a failure of **dimensionality**. It is what happens when high-dimensional human beings — with many partially independent beliefs, histories, identities, incentives, wounds, loyalties, and contradictions — are compressed into low-dimensional symbolic systems and then judged as if the projection were the person.

The curse of dimensionality, a concept well understood in mathematics and machine learning, has a social analogue that we have barely begun to recognise. It manifests not in data tables but in public discourse, moral judgement, political identity, and the experience of being seen by others.

Polarisation, in this framing, is **dimensionality collapse**.

---

## The human subject as a high-dimensional object

Consider a person. Not a demographic profile or a voter registration record, but an actual human being.

This person holds views on economic policy that were shaped by growing up in a household where money was unstable. They have a complicated relationship with institutional religion — drawn to the aesthetics and the community, alienated by the doctrine. They distrust pharmaceutical companies but vaccinate their children. They vote for a party whose cultural positions they find embarrassing. They were radicalised briefly in their twenties by a book they now find simplistic. They have a deep, inarticulate loyalty to a place. They are generous with individuals and suspicious of organisations. They hold contradictions they have never resolved and do not experience as contradictions.

This person is not a point on a line. They are a point in a space of enormous dimension.

Formally, represent this person as a vector:

$$x \in \mathbb{R}^n$$

where $$n$$ is large and each coordinate encodes something partially independent: an economic preference, a cultural affiliation, a class memory, an aesthetic sensibility, a religious impulse, a trauma response, a geographic loyalty, a relationship to authority, a tolerance for risk, a theory of human nature.

These dimensions are not neatly orthogonal, but they are not reducible to one another either. A person's position on immigration does not fully determine their position on monetary policy, which does not fully determine their relationship to tradition, which does not fully determine their theory of justice. The human being is not merely complex in a quantitative sense. It is **ontologically heterogeneous**: material, symbolic, historical, affective, economic, religious, familial, institutional, and existential dimensions coexist within a single subject, and they do not share a common metric.

This is where the trouble begins. Because society, in order to function at scale, must find ways to make people **legible**.

---

## Political identity as lossy compression

Every political system, every media ecosystem, every bureaucratic apparatus, every algorithmic platform performs the same fundamental operation: it takes the high-dimensional human and compresses them into something tractable.

Left or right. Progressive or conservative. Woke or anti-woke. Elite or people. Oppressor or oppressed. Rational or irrational. Us or them.

This is a compression function:

$$f: \mathbb{R}^n \rightarrow \mathbb{R}^k, \quad k \ll n$$

The output $$f(x)$$ is a political identity, a media profile, a demographic segment, a recommendation cluster, a moral category. It retains some information about the original vector $$x$$, but it necessarily discards most of it. The compression is **lossy**. It has to be. That is what compression means.

In the simplest and most brutal case, $$k = 1$$. The entire person is projected onto a single axis — a number line from left to right, from progressive to reactionary, from good to bad. This is the linear projection:

$$z = w^\top x$$

where $$w$$ is some weight vector that determines which dimensions of the person are amplified and which are silenced. The result is a scalar. A score. A position on a line.

The information loss is catastrophic.

The person who is fiscally conservative but socially liberal, culturally traditional but institutionally sceptical, economically anxious but interpersonally generous — this person does not survive the projection. They become a point on a line, and the line does not have room for them.

But the system proceeds as if it does.

---

## The curse of dimensionality as a curse of social legibility

In machine learning, the curse of dimensionality refers to a collection of phenomena that arise when data lives in high-dimensional spaces. Distances become unreliable. Points that appear close may be far apart; points that appear far apart may be neighbours. Clusters dissolve. Intuitions trained on two or three dimensions fail silently.

The social version of this curse is the following: **when complex agents are projected into simplified representational spaces, the geometry of human similarity is destroyed**.

Consider two people, $$x_i$$ and $$x_j$$, who are genuinely close in the original space — they share values, experiences, temperaments, even specific policy preferences. But they differ on one or two dimensions that happen to be heavily weighted in the current political projection. Perhaps one uses the language of social justice and the other does not. Perhaps one voted for a party the other finds contemptible. Perhaps one expresses their identical concern about inequality in economic terms and the other in cultural terms.

In the full space, they are neighbours:

$$d(x_i, x_j) \text{ is small}$$

In the compressed space, they are enemies:

$$d(f(x_i), f(x_j)) \text{ is large}$$

Conversely, two people who share almost nothing — different values, different experiences, different theories of the good — may find themselves projected onto the same point simply because they use the same vocabulary, vote for the same party, or are classified into the same cluster by an algorithm optimising for engagement.

This is **projection error**. It is not a bug in the system. It is the mathematically inevitable consequence of dimensionality reduction. When you compress a high-dimensional space into a low-dimensional one, you distort distances. You create artificial proximities and artificial oppositions. You see alliances where there is only coincidence, and you see enemies where there is only difference of expression.

Polarisation is not people becoming more different. It is people **appearing** more different because the space in which they are represented has collapsed.

---

## The alignment of formerly independent dimensions

One of the most telling signatures of polarisation is the progressive correlation of dimensions that have no intrinsic reason to be correlated.

In a healthy epistemic ecosystem, a person's position on tax policy should be largely independent of their position on vaccine mandates, which should be largely independent of their aesthetic preferences, which should be largely independent of their theory of gender, which should be largely independent of their feelings about cryptocurrency.

These are **independent dimensions**. In the original space, knowing someone's coordinate on one axis tells you little about their coordinate on another.

But under polarisation, something strange happens. The correlations increase:

$$\text{corr}(x_a, x_b) \rightarrow 1$$

Dimensions that were formerly independent become artificially aligned. If you know someone's position on climate policy, you can predict with disturbing accuracy their position on gun control, their feelings about academia, their dietary preferences, their opinion of a specific comedian, and their likelihood of using the word "problematic" in conversation.

This is not because these things are logically connected. It is because the compression function has **forced** them onto the same axis. The projection $$f$$ maps many independent dimensions onto a single coordinate, and in doing so it creates a phantom correlation structure that does not exist in the underlying reality.

In machine learning, this is a well-known artefact of aggressive dimensionality reduction. When you compress a dataset using too few principal components, you introduce spurious correlations between variables that are independent in the original space. The components mix signals that should remain separate. The resulting representation looks structured, but the structure is an artefact of the compression, not a feature of the data.

Polarisation does exactly this to people.

---

## Ideology as dimensionality reduction

An ideology, in this framing, is not primarily a set of beliefs. It is a **compression algorithm**. It is a function that takes the irreducible complexity of human experience and maps it onto a manageable number of dimensions — typically one or two.

The left-right axis is a principal component. It captures the largest single direction of variance in political opinion, but it does so by collapsing everything else. The second axis — authoritarian versus libertarian, or open versus closed — captures some additional variance, but the residual is still enormous.

What makes ideology powerful is not its accuracy but its **compression ratio**. It takes an $$n$$-dimensional object and renders it in $$k$$ dimensions, where $$k$$ is small enough for a human mind (or a media system, or an algorithm) to process quickly.

This is useful. Compression is useful. We cannot navigate a world of seven billion $$n$$-dimensional beings without some form of reduction. The question is not whether to compress, but whether we remember that we are compressing.

The ideologue is not someone who simplifies. Everyone simplifies. The ideologue is someone who has **forgotten that they are simplifying**. They mistake the compressed representation for the territory. They look at the low-dimensional projection and see, not a lossy summary, but reality itself.

This is the reification error: mistaking the projection for the real, the label for the life, the coordinate for the character.

---

## Algorithmic platforms as engines of compression

If ideology is dimensionality reduction performed by human minds, algorithmic platforms are dimensionality reduction performed at industrial scale, optimised not for accuracy but for engagement.

A social media platform observes a user — their clicks, their dwell time, their shares, their emotional reactions — and builds an embedding:

$$e_i = g(x_i)$$

This embedding lives in a latent space designed to predict behaviour. It does not need to be faithful to the person. It needs to be useful for the platform's objective function. And the objective function is engagement, which means the embedding is optimised to predict what will provoke a reaction.

Recommender systems then operate on these embeddings, surfacing content that is close in the latent space. But the latent space is not the human space. It is a compressed, distorted, commercially optimised projection of it.

The consequence is that the platform does not show you who people are. It shows you what its compression function has made of them. And because engagement is maximised by conflict, the compression function is biased toward dimensions that divide. Nuance is high-dimensional. Outrage is low-dimensional. A nuanced position occupies a specific, difficult-to-classify region of a high-dimensional space. An outraged position occupies an extreme on a single axis. The former is hard to recommend, hard to monetise, hard to mobilise. The latter is trivially classifiable, infinitely shareable, and algorithmically preferred.

The platform does not create polarisation from nothing. But it performs a specific operation: it takes the already lossy compression of political identity and compresses it further, selecting for the dimensions that maximise engagement and discarding the rest. It is a compression function applied to an already compressed signal. The distortion compounds.

---

## Extremes as attractors in compressed spaces

In a compressed representational space, the extremes are not merely positions. They are **attractors**.

Here is why. When a high-dimensional space is collapsed onto a single axis, the axis has two endpoints. These endpoints become the most legible, most classifiable, most socially reinforced positions in the space. They are the positions that the compression function can represent most faithfully, because they require the least information: you are maximally one thing. The centre, by contrast, is a region of high ambiguity in the compressed space — it could correspond to countless different positions in the original space, all of which have been mapped to the same indistinct middle.

This creates a dynamic where people are pulled toward the extremes not because they become more extreme in their actual views, but because the representational system rewards extremity with **legibility**. To be moderate in a polarised system is to be illegible. To be legible is to be classifiable. To be classifiable is to belong.

There is a feedback loop here. The compressed system classifies people. People, seeking legibility and belonging, begin to conform to the classification. The map starts shaping the territory. Categories that were imposed become identities that are inhabited. The projection, which was originally a lossy summary of a complex reality, becomes a mould into which reality is poured.

This is not conspiracy. It is the ordinary dynamics of classification systems interacting with social agents who are sensitive to how they are classified.

---

## The violence of pointing from inside the projection

Here is where the argument becomes, I think, genuinely dangerous to comfortable moral positions.

The most destructive feature of polarisation is not that people disagree. It is that people **point at others from inside a reduced coordinate system without realising they are performing dimensionality reduction**.

They observe one coordinate — a vote, a word, a cultural affiliation, a social media post — and infer the whole vector. They see a point on a line and mistake it for a soul.

The sentence "I know what kind of person you are" almost always means: "I know where my model places you." It is a statement about the speaker's compression function, not about the other person's reality. But it is experienced as direct perception. The model is invisible to the person using it.

This is how polarisation produces cruelty while feeling righteous. The accuser is not lying. Within their compressed representation, their judgement is consistent. They see a person located at a specific point on their axis, and they respond to that point with the full moral weight they believe it deserves. The problem is that the point is not the person. The person has been collapsed, and the collapsed version is being punished for crimes that belong to the projection.

Consider the mapping:

$$\text{person} \rightarrow \text{label}$$

$$\text{life} \rightarrow \text{signal}$$

$$\text{history} \rightarrow \text{type}$$

$$\text{contradiction} \rightarrow \text{hypocrisy}$$

$$\text{complexity} \rightarrow \text{enemy}$$

Each of these is a lossy compression. The person has a life; the label has a valence. The person has a history; the type has a file. The person contains contradictions; the compressed version reads these as hypocrisy, because in a one-dimensional space, holding two positions means occupying two points on the same line, which looks like dishonesty. But in the original space, those positions may not be on the same axis at all.

The polarised person does not merely simplify the other. They **forget that they have simplified them**. And this forgetting is what allows category violence — the violence of treating a human being as an instance of a category — to be experienced as moral clarity.

---

## Moral certainty as dimensional blindness

Moral certainty, in a polarised context, is often not the presence of insight but the **absence of dimensions**.

When you can see only one axis, the world looks extraordinarily clear. Good and evil are distributed along a line. Everyone has a location. The location determines their moral status. There is nothing to be confused about.

This clarity is real, but it is the clarity of a projection, not of the thing projected. It is the clarity you get from a shadow cast on a wall: sharp, definite, and missing a dimension. Plato understood this.

The person who is morally certain in a polarised environment is often someone for whom the compression function has become invisible. They do not experience themselves as looking at a low-dimensional representation. They experience themselves as looking at reality. The map has fully replaced the territory.

This is why moral certainty and cruelty so often travel together. Not because certainty causes cruelty, but because dimensional blindness removes the perceptual apparatus that would otherwise make cruelty visible as cruelty. If you cannot see the dimensions along which the other person is a full human being — the dimensions that your projection has discarded — then you cannot see the damage you are doing to those dimensions. You are not being cruel. You are being **precise**. The precision is an artefact of the collapse.

---

## The accuser is also compressed

There is a temptation, at this point in the argument, to imagine oneself as the person who sees the full dimensionality while others are trapped in their projections. This temptation must be resisted.

The accuser — the person who points at the other and says *you are reducible to this label* — is also a high-dimensional being who has been compressed. Often by the same system. Often by their own act of accusation.

To point at someone from inside a political identity is to accept, at least momentarily, the coordinate system that makes that pointing possible. The act of accusation compresses both the accused and the accuser. It forces both into the same low-dimensional space.

This is why polarised arguments feel so claustrophobic. Not because the people involved are stupid or malicious, but because the representational space in which the argument occurs is too small to contain them. Both parties are larger than the argument allows. Both are being flattened by the very structure of the confrontation.

Both sides often accuse each other from inside different projections of a higher-dimensional object. They are not looking at the same thing and disagreeing. They are looking at different shadows of the same thing and arguing about which shadow is real. The answer, of course, is neither. The shadows are both accurate, both incomplete, and both incapable of recognising their own incompleteness from within.

---

## Polarisation as an ontological condition

I have been describing polarisation as an epistemological problem — a failure of representation, a distortion of knowledge. But I think it is also an **ontological** condition. Under polarisation, the world itself begins to appear lower-dimensional.

Not because reality has simplified, but because the perceptual and institutional systems through which reality is apprehended have narrowed. When every event is filtered through a single axis — is this good for our side or theirs? — the richness of the event is not merely ignored. It becomes **invisible**. The dimensions that have been discarded from the representational space do not appear as missing. They simply do not appear.

This is the deepest form of the curse. It is not that polarised people are aware of the complexity and choose to ignore it. It is that the compression has become so total, so habitual, so institutionally reinforced, that the discarded dimensions are no longer perceptible. The polarised subject mistakes low-dimensional legibility for truth. The world really does look this simple. It is not an act.

And this is why arguments fail. You cannot show someone a dimension they do not have. You cannot point to something that exists outside their coordinate system by giving it coordinates within that system. The missing dimensions are, by definition, orthogonal to the space in which the conversation is occurring.

---

## Depolarisation as restoring dimensionality

If polarisation is dimensionality collapse, then depolarisation cannot be achieved by simply asking people to be nicer, more tolerant, or more willing to listen. These are moral exhortations directed at a structural problem. They are like asking a two-dimensional projection to become three-dimensional through goodwill.

Depolarisation requires **restoring dimensions**.

This means creating conditions under which people encounter each other in ways that are not mediated by the dominant compression function. It means building institutions that are not legible along a single axis. It means designing information environments that resist the collapse of independent dimensions into correlated clusters. It means cultivating the cognitive and emotional capacity to hold high-dimensional representations of other people — to resist the seductive clarity of the projection.

Concretely, this might mean:
- Encountering people through roles and contexts that cut across political identity — as neighbours, as collaborators on local problems, as members of overlapping communities that do not align with partisan categories.
- Building media systems that reward multi-dimensional representation rather than engagement-optimised simplification.
- Recognising that the feeling of moral clarity in a polarised context is a diagnostic signal, not a trustworthy guide. When the world looks perfectly legible, when every person can be placed on a line, when the other side is obviously wrong — that is the moment to suspect that dimensions have been discarded.

The goal is not consensus. The goal is not even agreement. The goal is a representational space rich enough to contain the people it claims to describe.

---

## Final thesis

Polarisation is the collapse of a many-dimensional human world into a line. It is the process by which the irreducible complexity of persons — their layered histories, their partial loyalties, their unresolved contradictions, their orthogonal commitments — is compressed into a coordinate on a single axis and then treated as if the coordinate were the person.

This compression is performed by ideologies, by institutions, by algorithms, by media systems, and by human minds under pressure to make the world legible. It is not always malicious. It is sometimes necessary. But when it is mistaken for perception rather than recognised as reduction, it produces a specific and devastating pathology: people begin to see each other as points on a line, and they respond to the points with the moral weight that only the full-dimensional human deserves.

The cure for polarisation is not the abolition of disagreement. Disagreement is high-dimensional; it requires the full space to express itself faithfully. The cure is the recovery of lost dimensions. A society is healthy not when everyone agrees, but when no single axis is allowed to exhaust the human.
