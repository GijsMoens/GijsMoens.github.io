---
layout: post
title: "Polarisation as Dimensionality Collapse"
date: 2026-06-01 10:00:00
description: Polarisation is not disagreement. It is what happens when high-dimensional human beings are compressed into low-dimensional symbolic systems and then judged as if the projection were the person.
tags: polarisation dimensionality-reduction systems-thinking philosophy machine-learning
categories: Weekly-Thoughts Non-Technical
---

The standard diagnosis of polarisation goes something like this: people are becoming more extreme, more tribal, less empathetic. They retreat into echo chambers. They have forgotten how to talk to each other. If only they would listen.

This diagnosis is not wrong. It is worse than wrong. It is boring. It describes symptoms while sounding profound, which is the rhetorical equivalent of diagnosing a fever by noting that the patient feels warm.

Here is a different claim. Polarisation is not primarily a failure of empathy, civility, or rationality. It is a failure of **dimensionality**. It is what happens when high-dimensional human beings, with many partially independent beliefs, histories, identities, incentives, wounds, loyalties, and contradictions, are compressed into low-dimensional symbolic systems and then judged as if the projection were the person.

The curse of dimensionality, a concept well understood in mathematics and machine learning, has a social analogue that we have barely begun to take seriously. It shows up not in data tables but in public discourse, moral judgement, political identity, and the experience of being seen. Or rather, of being *approximately* seen.

Polarisation, in this framing, is **dimensionality collapse**.

---

## The human subject as a high-dimensional object

Consider a person. Not a demographic profile or a voter registration record or a Twitter bio. An actual human being.

This person holds views on economic policy shaped by growing up in a household where money was unstable. They have a complicated relationship with institutional religion: drawn to the aesthetics and the community, alienated by the doctrine, privately furious about the politics, but they still go at Christmas and they are not entirely sure why. They distrust pharmaceutical companies but vaccinate their children. They vote for a party whose cultural positions they find embarrassing but whose economic instincts roughly match their own, which they find embarrassing in a different way. They were radicalised briefly in their twenties by a book they now find simplistic but still quote at dinner parties. They have a deep, inarticulate loyalty to a place. They are generous with individuals and suspicious of organisations. They think modern art is mostly a money-laundering operation but cried at a Rothko once and have never told anyone.

They hold contradictions they have never resolved and do not experience as contradictions, because they live in all their dimensions simultaneously. Which is what living is.

This person is not a point on a line. They are a point in a space of enormous dimension.

Formally, represent this person as a vector:

$$x \in \mathbb{R}^n$$

where $$n$$ is large and each coordinate encodes something partially independent: an economic preference, a cultural affiliation, a class memory, an aesthetic sensibility, a religious impulse, a trauma response, a geographic loyalty, a relationship to authority, a tolerance for risk, a theory of human nature, an opinion on whether a hot dog is a sandwich.

These dimensions are not neatly orthogonal, but they are not reducible to one another either. A person's position on immigration does not fully determine their position on monetary policy, which does not fully determine their relationship to tradition, which does not fully determine their theory of justice, which tells you nothing whatsoever about whether they think the moon landing was faked. The human being is not merely complex in a quantitative sense. It is **ontologically heterogeneous**: material, symbolic, historical, affective, economic, religious, familial, institutional, and existential dimensions coexist within a single subject. They do not share a common metric.

This is where the trouble begins. Society, in order to function at scale, must find ways to make people **legible**. And legibility has a cost measured in dimensions.

---

## Political identity as lossy compression

Every political system, every media ecosystem, every bureaucratic apparatus performs the same fundamental operation on the human being: it makes them smaller.

Left or right. Progressive or conservative. Woke or anti-woke. Elite or people. Oppressor or oppressed. Us or them. Pick one. You have five seconds.

This is a compression function:

$$f: \mathbb{R}^n \rightarrow \mathbb{R}^k, \quad k \ll n$$

The output $$f(x)$$ is a political identity, a media profile, a demographic segment, a moral category. It retains some information about the original vector $$x$$, but it necessarily discards most of it. The compression is **lossy**. That is what compression means. The question is never whether information is lost, but which information, and whether anyone notices.

In the simplest and most brutal case, $$k = 1$$. The entire person is projected onto a single axis, a number line from left to right, from progressive to reactionary, from enlightened to deplorable:

$$z = w^\top x$$

where $$w$$ is some weight vector that determines which dimensions of the person are amplified and which are silenced. The result is a scalar. A score. A position on a line. A place in the queue for moral judgement.

The person who is fiscally conservative but socially liberal, culturally traditional but institutionally sceptical, economically anxious but interpersonally generous, who listens to both country music and NPR and sees no tension in this: this person does not survive the projection. They become a point on a line, and the line does not have room for them.

But the system proceeds as if it does.

---

## The curse of dimensionality as a curse of social legibility

In machine learning, the curse of dimensionality refers to a collection of phenomena that arise when data lives in high-dimensional spaces. Distances become unreliable. Points that appear close may be far apart. Points that appear far apart may be neighbours. Intuitions trained in low dimensions fail silently and confidently.

The social version of this curse: **when complex agents are projected into simplified representational spaces, the geometry of human similarity is destroyed**.

Consider two people, $$x_i$$ and $$x_j$$, who are genuinely close in the original space. They share values, experiences, temperaments, even specific policy preferences. They would get along. They would agree on almost everything that matters in a life. But they differ on one or two dimensions that happen to be heavily weighted in the current political projection. Perhaps one uses the language of social justice and the other does not. Perhaps one voted for a party the other finds contemptible. Perhaps one expresses their identical concern about inequality in economic terms and the other in cultural terms, and neither recognises the other's dialect.

In the full space, they are neighbours:

$$d(x_i, x_j) \text{ is small}$$

In the compressed space, they are enemies:

$$d(f(x_i), f(x_j)) \text{ is large}$$

Conversely, two people who share almost nothing (different values, different experiences, different theories of the good, different ideas about what constitutes a reasonable bedtime) may find themselves projected onto the same point simply because they use the same vocabulary, vote for the same party, or post the same memes.

This is **projection error**. It is not a bug. It is the mathematically inevitable consequence of dimensionality reduction. Compress a high-dimensional space into a low-dimensional one and you distort distances. You create artificial proximities and artificial oppositions. You manufacture alliances out of coincidence and enemies out of dialect.

Polarisation is not people becoming more different. It is people **appearing** more different because the space in which they are represented has collapsed.

---

## The alignment of formerly independent dimensions

One of the most telling signatures of polarisation, and one of the strangest once you see it, is the progressive correlation of dimensions that have no intrinsic reason to be correlated.

In a healthy epistemic ecosystem, a person's position on tax policy should be largely independent of their position on vaccine mandates, which should be largely independent of their aesthetic preferences, which should be largely independent of their theory of gender, which should be largely independent of their feelings about cryptocurrency, which should be largely independent of their opinion on whether it is acceptable to recline your seat on a short-haul flight. These are **independent dimensions**. In the original space, knowing someone's coordinate on one axis tells you almost nothing about their coordinate on another.

But under polarisation, something strange happens. The correlations increase:

$$\text{corr}(x_a, x_b) \rightarrow 1$$

Dimensions that were formerly independent become artificially aligned. If you know someone's position on climate policy, you can predict with disturbing accuracy their position on gun control, their feelings about academia, their dietary preferences, their opinion of a specific comedian, their likelihood of using the word "problematic" in conversation, whether they own a pickup truck, and which streaming service they consider morally superior. Tell me your view on pronouns and I will tell you your view on central banking. This should be bizarre. It is treated as natural.

This is not because these things are logically connected. It is because the compression function has **forced** them onto the same axis. The projection $$f$$ maps many independent dimensions onto a single coordinate, and in doing so it creates a phantom correlation structure that does not exist in the underlying reality. A hallucination of structure. The political equivalent of seeing a face in a cloud, except the face is wearing a red hat or a rainbow pin and everyone is arguing about its expression.

In machine learning, this is a well-known artefact of aggressive dimensionality reduction. Compress a dataset using too few principal components and you introduce spurious correlations between variables that are independent in the original space. The components mix signals that should remain separate. The resulting representation looks structured, but the structure is an artefact of the compression, not a feature of the data.

Polarisation does exactly this to people. It takes the uncorrelated mess of actual human opinion and irons it into bundles. Then it treats the bundles as ideologies, as if the bundling were a discovery rather than an imposition.

---

## Ideology as dimensionality reduction

An ideology, in this framing, is not primarily a set of beliefs. It is a **compression algorithm**. A function that takes the irreducible complexity of human experience and maps it onto a manageable number of dimensions. Typically one or two, because that is the most a slogan can hold.

The left-right axis is a principal component. It captures the largest single direction of variance in political opinion, but it does so by collapsing everything else. The second axis (authoritarian versus libertarian, or open versus closed) captures some additional variance. The residual is still enormous. Most of the person is in the residual. The residual does not get a vote.

What makes ideology powerful is not its accuracy but its **compression ratio**. It takes an $$n$$-dimensional object and renders it in $$k$$ dimensions, where $$k$$ is small enough for a headline, a hashtag, or a campaign button. This is useful. We cannot navigate a world of eight billion $$n$$-dimensional beings without some form of reduction. The question is not whether to compress, because that is not optional, but whether we remember that we are compressing.

The ideologue is not someone who simplifies. Everyone simplifies. The person who claims to reject ideology is simply running an unlabelled compression function and calling the output "common sense." The ideologue, more precisely, is someone who has **forgotten that they are simplifying**. They mistake the compressed representation for the territory. They look at the low-dimensional projection and see not a lossy summary, but reality itself.

This is the reification error: mistaking the projection for the real, the label for the life, the coordinate for the character.

The most natural error in the world. Also one of the most expensive.

---

## Extremes as attractors in compressed spaces

In a compressed representational space, the extremes are not merely positions. They are **attractors**.

When a high-dimensional space is collapsed onto a single axis, the axis has two endpoints. These endpoints become the most legible, most classifiable, most socially reinforced positions available. They are the positions that the compression function can represent most faithfully, because they require the least information: you are maximally one thing. The centre, by contrast, is a region of high ambiguity. It could correspond to countless different positions in the original space, all mapped to the same indistinct middle. The moderate is not moderate because they lack conviction. They are illegible because the representational system lacks the bandwidth to express what they actually think.

People drift toward the extremes not because they become more extreme in their actual views, but because the representational system rewards extremity with **legibility**. To be moderate in a polarised system is to be perpetually misread. To be extreme is to be instantly classifiable. To be classifiable is to belong. And belonging, for a social species, is not a trivial incentive. It might be the incentive.

The feedback loop deserves careful attention. The compressed system classifies people. People, seeking legibility and belonging, begin to conform to the classification. The map starts shaping the territory. Categories that were imposed become identities that are inhabited. The projection, which was originally a lossy summary of a complex reality, becomes a mould into which reality is poured. People start saying things they half-believe because the things they fully believe do not fit on the axis. Eventually, they forget which beliefs were original and which were adopted for legibility. The compression becomes the person. That is the endgame.

---

## The violence of pointing from inside the projection

Here is where the argument becomes uncomfortable for anyone who has ever been certain about another person's character on the basis of limited information. Which is everyone. Including, to be clear, the author.

The most destructive feature of polarisation is not that people disagree. It is that people **point at others from inside a reduced coordinate system without realising they are performing dimensionality reduction**.

They observe one coordinate (a vote, a word, a cultural affiliation, a bumper sticker, a dietary choice, a social media post made at 11pm after two glasses of wine) and infer the whole vector. They see a point on a line and mistake it for a soul.

The sentence "I know what kind of person you are" almost always means: "I know where my model places you." It is a statement about the speaker's compression function, not about the other person's reality. But it is experienced as direct perception. The model is invisible to the person using it. It always is.

This is how polarisation produces cruelty while feeling righteous. The accuser is not lying. Within their compressed representation, their judgement is consistent. They see a person located at a specific point on their axis, and they respond to that point with the full moral weight they believe it deserves. The problem is that the point is not the person. The person has been collapsed, and the collapsed version is being punished for crimes that belong to the projection.

The person has a life; the label has a valence. The person has a history; the type has a file. The person contains contradictions that coexist peacefully across multiple dimensions; the compressed version reads these as hypocrisy, because in a one-dimensional space, holding two positions means occupying two points on the same line, which looks like dishonesty. In the original space, those positions may not be on the same axis at all. They may be as unrelated as a preference for sourdough and a theory of property rights. But the compression function does not care. It has one axis and it will use it.

The polarised person does not merely simplify the other. They **forget that they have simplified them**. And this forgetting is what allows category violence (the violence of treating a human being as an instance of a category) to be experienced as moral clarity. The cruelty feels precise. That is what makes it cruel.

---

## Moral certainty as dimensional blindness

Moral certainty, in a polarised context, is often not the presence of insight but the **absence of dimensions**.

When you can see only one axis, the world looks extraordinarily clear. Good and evil are distributed along a line. Everyone has a location. The location determines their moral status. There is nothing to be confused about. The feeling is exhilarating. It is the exhilaration of a person who has finally cleaned their desk by throwing everything into a single drawer.

This clarity is real, but it is the clarity of a projection, not of the thing projected. The clarity you get from a shadow cast on a wall: sharp, definite, and missing a dimension. Plato understood this. He also understood that the people watching the shadows would not thank you for pointing out the fire.

The person who is morally certain in a polarised environment is typically someone for whom the compression function has become invisible. They do not experience themselves as looking at a low-dimensional representation. They experience themselves as seeing things clearly, perhaps for the first time. The map has replaced the territory so completely that pointing out the substitution feels like an attack on reality itself.

This is why moral certainty and cruelty so often travel together. Not because certainty causes cruelty, but because dimensional blindness removes the perceptual apparatus that would otherwise make cruelty visible as cruelty. If you cannot see the dimensions along which the other person is a full human being (the dimensions your projection has discarded) then you cannot see the damage you are doing to those dimensions. You are not being cruel. You are being **precise**. The precision is an artefact of the collapse. But it feels like truth.

---

## The accuser is also compressed

There is a temptation, at this point in the argument, to imagine oneself as the person who sees the full dimensionality while others are trapped in their projections. This temptation is itself a compression. Resist it.

The accuser, the person who points at the other and says *you are reducible to this label*, is also a high-dimensional being who has been compressed. Often by the same system. Often by their own act of accusation. The moment you reduce someone else to a point on your axis, you have implicitly accepted the axis. You have agreed to play in $$\mathbb{R}^k$$. You are now also $$k$$-dimensional. Congratulations.

To point at someone from inside a political identity is to accept the coordinate system that makes that pointing possible. The act of accusation compresses both the accused and the accuser. It forces both into the same low-dimensional space. This is why polarised arguments feel so claustrophobic. Not because the people involved are stupid or malicious, but because the representational space in which the argument occurs is too small to contain them. Both parties are larger than the argument allows. Both are being flattened by the very structure of the confrontation. Put them in any context where the axis is not operative and they would probably get along fine. They might even like each other. This is known. It is also consistently ignored.

Both sides often accuse each other from inside different projections of a higher-dimensional object. They are not looking at the same thing and disagreeing. They are looking at different shadows of the same thing and arguing about which shadow is real. The answer is neither. But you cannot say that from inside either shadow without sounding like you are defending the other one.

---

## Polarisation as an ontological condition

Polarisation is not only an epistemological problem, a failure of representation and a distortion of knowledge. It is also an **ontological** condition. Under sustained polarisation, the world itself begins to appear lower-dimensional.

Not because reality has simplified, but because the perceptual and institutional systems through which reality is apprehended have narrowed. When every event is filtered through a single axis (is this good for our side or theirs?) the richness of the event is not merely ignored. It becomes **invisible**. The discarded dimensions do not appear as missing. They simply do not appear. You do not notice the absence of something you have no coordinate for. This is true of colours, of sounds, and of other people's inner lives.

This is the deepest form of the curse. The compression has become so total, so habitual, so institutionally reinforced, that the discarded dimensions are no longer perceptible. The polarised subject mistakes low-dimensional legibility for truth. The world really does look this simple to them. It is not an act. That is precisely what makes it so hard to undo.

And this is why arguments fail. You cannot show someone a dimension they do not have. You cannot point to something that exists outside their coordinate system by giving it coordinates within that system. The missing dimensions are, by definition, orthogonal to the space in which the conversation is occurring. You are trying to point up in a world that only has left and right.

---

## Depolarisation as restoring dimensionality

If polarisation is dimensionality collapse, then depolarisation cannot be achieved by asking people to be nicer. That is a moral exhortation directed at a structural problem. Like asking a two-dimensional projection to become three-dimensional through goodwill.

Depolarisation requires **restoring dimensions**. It means creating conditions under which people encounter each other in ways not mediated by the dominant compression function: as neighbours, as collaborators on problems that refuse to map onto the axis, as members of communities whose boundaries cut across partisan lines rather than along them. It means cultivating the capacity to hold high-dimensional representations of other people, which is uncomfortable, because high-dimensional representations are ambiguous, and ambiguity is the thing that compression was designed to eliminate.

Most importantly, it means recognising that the feeling of moral clarity in a polarised context is a diagnostic signal, not a trustworthy guide. When the world looks perfectly legible, when every person can be placed on a line, when the other side is obviously and comprehensively wrong: that is the moment to suspect that dimensions have been discarded. Clarity that total is almost never a property of reality. It is a property of the projection.

The goal is not consensus. Not even agreement. The goal is a representational space rich enough to contain the people it claims to describe.

---

## Final thesis

Polarisation is the collapse of a many-dimensional human world into a line. It is the process by which the irreducible complexity of persons, their layered histories, their partial loyalties, their unresolved contradictions, their orthogonal commitments, their inexplicable music taste, is compressed into a coordinate on a single axis and then treated as if the coordinate were the person.

This compression is performed by ideologies, by institutions, by media systems, and by human minds under pressure to make the world legible. It is not always malicious. It is sometimes necessary. But when it is mistaken for perception rather than recognised as reduction, it produces a specific and devastating pathology: people begin to see each other as points on a line, and they respond to the points with the moral weight that only the full-dimensional human deserves.

The cure for polarisation is not the abolition of disagreement. Disagreement is high-dimensional; it requires the full space to express itself faithfully. The cure is the recovery of lost dimensions. A society is healthy not when everyone agrees, but when no single axis is allowed to exhaust the human.
