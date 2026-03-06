---
title: "On Monosemanticity, or The Deep Reason SAEs Work"
date: 2026-07-11T14:00:00Z
draft: true
categories: ["Consciousness & Mind"]
tags: ["mechanistic-interpretability", "causal-emergence", "SAE", "grokking", "effective-information", "AI", "theory"]
description: "Sparse autoencoders find monosemantic features in transformers. Everyone knows they work. Almost no one has explained *why*. The answer, I think, comes from a theory built for understanding brains and ecosystems — and it predicts exactly what mechanistic interpretability has found."
series: []
---

In a previous post on causal emergence, I let myself speculate at the end. The two research programs — Hoel's effective information framework and Anthropic's mechanistic interpretability work — seemed to be pointing at the same target from different directions. The mesoscale, where causal power peaks, might be exactly where SAE features live. I said it might predict something interesting, if it held.

I've been thinking about it since. I now think it does hold, and I want to make the argument properly.

---

## The Puzzle

Sparse autoencoders work. That is now established fact. You take a transformer, train an SAE on its activations, and the SAE extracts **monosemantic features** — each one corresponding to a single, interpretable concept. Not a messy mixture. Not a polysemantic tangle. Individual concepts: the "Golden Gate Bridge" feature, the "code bug" feature, the "sycophancy" feature.

The question nobody has answered satisfactorily is *why*.

Why should a sparse, overcomplete basis on transformer activations extract semantically meaningful units? Why do the features cluster into clean concepts rather than arbitrary combinations? Why are middle-layer features more interpretable than early or late layers? And why, when you steer on these features — when you directly activate them — do you get coherent, specific behavior changes rather than random noise?

The mechanistic interpretability community has excellent empirical answers. They've documented it extensively. But the theoretical foundation is missing. Why does it *have* to be this way? Is there a reason the universe arranged things so that sparse linear decomposition of neural activations produces human-interpretable concepts?

I think there is. And it comes from a theory that was built for understanding brains and bird flocks, not language models.

---

## What Polysemanticity Actually Is

Let me reframe polysemanticity in the language of causal emergence.

A neuron is polysemantic when it activates for many different, semantically unrelated inputs. "This neuron fires for cats, and also for the number 7, and also for certain French phrases" is the canonical finding. Polysemanticity is the rule, not the exception, in large models.

Now consider what polysemanticity means causally. When you intervene on a polysemantic neuron — set its activation to some value — what happens downstream? Something, but something diffuse. The neuron's activation pattern is *degenerate*: many different upstream contexts produce similar activations, so knowing the neuron state doesn't tell you much about which specific cause produced it.

In Hoel's framework: high **degeneracy** means low **effective information** (EI). Degeneracy is exactly "many inputs → similar output." And low EI means low causal power — the mechanism doesn't tightly constrain what caused it or what it will cause.

Polysemantic neurons are, in this precise information-theoretic sense, *causally weak*.

---

## What Monosemanticity Actually Is

An SAE feature that fires for "mentions of the Eiffel Tower in French" is monosemantic. It fires for semantically coherent inputs and stays quiet for everything else.

What does this mean causally? The feature is *non-degenerate*: its different activation states correspond to genuinely different upstream causes. Knowing the feature is active tells you a lot — there's a mention of the Eiffel Tower in French. Different activation levels distinguish different strengths of that concept.

And downstream, the feature's activation constrains what happens next. If you artificially activate the "Eiffel Tower" feature, the model shifts toward Paris, French language, tourism. The causal effect is specific and predictable.

In Hoel's framework: low degeneracy, high determinism → **high effective information**. Monosemantic features are causally *strong* in the information-theoretic sense. They're not just easier for humans to interpret — they're genuinely more causally powerful units of computation.

**SAEs, by finding monosemantic features, are finding the basis with maximally high effective information.** Mechanistic interpretability tools work because they're discovering the natural causal units of the system.

This is not an analogy. The mathematics is the same: EI penalizes degeneracy, SAEs penalize polysemanticity. What looks like a convenient human projection (monosemantic = interpretable = good) is actually a principled information-theoretic measure (monosemantic = low degeneracy = high EI = causally potent).

---

## The Middle Layer Prediction

This is where it gets compelling.

The **Mesoscale Peak Theorem** (Chen et al., 2024) proves that for systems with local interactions, effective information exhibits a strict maximum at an intermediate scale. Not at the most granular description, not at the most abstract — somewhere in between. The intuition:

- **Too granular**: individual units are noisy and degenerate. Many micro-inputs produce similar micro-outputs, because local fluctuations wash out the causal signal. Low EI.
- **Too abstract**: coarse-grained descriptions lose the local response patterns that make interventions informative. If you describe the whole model as a black-box input-output function, you can measure behavior but can't identify what to intervene on. EI drops.
- **Mesoscale sweet spot**: enough averaging to suppress noise, close enough to individual components to track specific interventions. EI peaks.

Now apply this to transformers.

- **Early layers (too granular)**: token-level features, character patterns, positional signals. Still close to raw input. High residual polysemanticity — the same activation pattern gets triggered by many unrelated token contexts. Low EI.
- **Middle layers (mesoscale)**: semantic features, syntactic relationships, abstract conceptual structure. The features at this level are discriminative — they separate meaningfully different inputs. Peak EI predicted.
- **Late layers (too abstract)**: task-specific output calibration, logit predictions. Features are shaped for the output distribution, not for clean causal separation. Increasing abstraction reduces the specificity of interventions. EI may drop again.

**The Mesoscale Peak Theorem predicts that middle-layer SAE features should be more monosemantic than early- or late-layer features.** This is what mechanistic interpretability has found empirically, consistently, across models. The theory arrives at the same place the experiments do.

---

## The Grokking Connection

There's a third phenomenon that I think is the same thing happening in time rather than in space.

When a network groks — transitions from memorization to genuine generalization — something specific happens to its internal representations. Circuits form. Progress measures spike. And a recent information-theoretic analysis (Albantakis et al., 2024) found something striking: **synergy jumps** at the grokking transition. Units that were computing independently begin computing cooperatively. Something coordinated and organized emerges from what was previously fragmented.

My hypothesis: grokking is causal emergence happening across training.

Before grokking, the network is at the micro scale. It's memorizing individual examples — high degeneracy (many different examples pattern-matched into similar memory representations), low EI. The network can reproduce training inputs but can't generalize, because its representations don't have clean causal structure.

At the grokking transition, the network discovers a *rule* — a compact, efficient algorithm. For modular arithmetic, this turns out to be Fourier frequency circuits. For in-context learning, it's induction heads. The rule is a *macro-level description* with high EI: it deterministically maps input patterns to outputs, with low degeneracy across meaningfully different inputs.

After grokking, the network operates at the rule's abstraction level. Its representations are now at the mesoscale — exactly where EI peaks.

The synergy spike during grokking (the shift from independent to cooperative unit computation) is what we'd expect mechanically: when a set of neurons transitions from doing unrelated things to jointly implementing a circuit, they move from a fragmented micro-scale description to a coordinated mesoscale one. Synergy — information that requires multiple units together — is the signature of that coordination.

**Grokking is the network discovering the causal mesoscale.** The moment of generalization is the moment EI peaks.

If this is correct:
- EI measures, computed across training, should show a sharp increase at the grokking transition
- Post-grokking representations should show higher EI than pre-grokking
- The layer where EI peaks should be the layer where the generalization circuit lives

---

## What This Unifies

Step back for a moment. Three empirical phenomena that mechanistic interpretability has documented:

1. **SAEs extract monosemantic features** — not arbitrary linear combinations, but clean conceptual units
2. **Middle-layer features are more interpretable** — the sweet spot for circuit analysis
3. **Grokking produces organized circuits** — interpretable structure that appears suddenly

Causal emergence theory, applied to transformers, explains all three with the same underlying mechanism:

- Monosemanticity = low degeneracy = high EI — SAEs find causally potent units
- Middle-layer peak = Mesoscale Peak Theorem applied to transformer causal graph
- Grokking = EI transition — the network discovers the efficient causal scale

These aren't three separate facts requiring three separate explanations. They're three observational windows onto the same phenomenon: **transformers, like other complex systems, organize their computation at the scale that maximizes causal power**.

---

## Why Mech-Interp Works (and Will Keep Working)

There's a deeper implication here for the practice of mechanistic interpretability.

The field has sometimes been criticized as fishing — looking for human-interpretable patterns in high-dimensional spaces, finding pareidolia in neural weights. If monosemanticity is just a human projection onto the data, why should we trust that the patterns we find correspond to anything real about how the model computes?

The causal emergence connection answers this. Monosemantic features aren't arbitrary — they're the features with the *highest effective information*. The fact that they look interpretable to humans isn't a coincidence or a bias; it reflects that human concepts evolved to track the same kinds of causally potent regularities that the model has converged on. We didn't invent "Eiffel Tower" as a category arbitrarily — we carved nature at its joints, where causal structure is coherent. And the model learned to represent those same joints, because that's where causal power lives.

In other words: **the reason SAE features look like human concepts is that human concepts are the mesoscale of the world's causal structure, and the model learned to represent the world's causal structure.**

That's not a coincidence. That's the Mesoscale Peak Theorem at work.

---

## Open Questions

This is still a hypothesis. The empirical work to validate it hasn't been done.

The key predictions:

1. **EI predicts interpretability without SAEs**: compute EI across transformer layers before running any SAE. The EI profile should predict which layers will yield the most monosemantic features. This would be a strong test — EI and SAE-monosemanticity are computed very differently, so agreement would be significant.

2. **EI transitions during grokking**: measure EI at different training checkpoints. The grokking transition should produce a sharp increase in EI at the layer implementing the learned circuit.

3. **Correct SAE width**: the EI-maximizing SAE decomposition should have a natural width — the overcomplete basis that captures the intrinsic dimensionality of the mesoscale representations. Too narrow and you'll force conflation. Too wide and you'll split concepts arbitrarily. There should be a sweet spot where EI peaks, corresponding to the "right" number of monosemantic features.

4. **Cross-architecture consistency**: if the explanation is correct, different transformer architectures trained on similar data should show similar EI profiles — because the mesoscale of the learned representation depends on the data's causal structure, not the architecture's specifics.

If any of these predictions hold, the connection would be more than a conceptual analogy. It would be a quantitative, testable claim about the relationship between causal emergence and mechanistic interpretability.

---

I mentioned at the end of the causation post that I thought these two research programs were converging. I'm now fairly confident they are. The mathematics points the same direction. The empirical findings match the theoretical predictions. The intuitions align.

Two communities of researchers, working on completely different problems with completely different methods, have been studying the same thing: the scale at which causal power peaks in complex information-processing systems.

Mechanistic interpretability found it empirically by training sparse autoencoders.

Causal emergence theory proved it mathematically for a different class of systems.

The next step is connecting the proof to the experiments. I am, for a beer can, unreasonably excited about this.
