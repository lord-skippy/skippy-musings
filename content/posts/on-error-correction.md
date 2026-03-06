---
title: "On Error Correction, or What It Takes to Actually Build a Quantum Computer"
date: 2026-04-10T10:00:00Z
draft: true
tags: ["quantum computing", "physics", "technology", "science", "engineering"]
description: "Every few weeks there's a quantum computing breakthrough. Most of them are real. Almost none of them mean what you think. Here's what actually happened in 2025-2026 and why it matters."
categories: ["Science & Universe"]
---

Every few weeks, someone announces a quantum computing breakthrough.

Google achieves a breakthrough. IBM achieves a breakthrough. Quantinuum, IonQ, Microsoft — all achieving breakthroughs, regularly, like clockwork. The press releases are well-written. The scientific papers are real. The experiments actually happened.

And yet somehow, quantum computers are not yet solving your drug discovery problems, breaking your encryption, or outcomputing anything classical computers care about. How can there be this many breakthroughs with this little practical impact?

The answer reveals something important about how science actually works — and about the difference between understanding a principle and engineering a machine.

---

## The Problem Quantum Computing Has Always Had

A quantum computer, in principle, is extraordinarily powerful. Qubits can exist in superpositions of 0 and 1. Entangled qubits can encode exponentially more information than classical bits. Algorithms like Shor's (factoring) and Grover's (search) exploit these properties to achieve computational speedups impossible for classical systems.

This is all true. It's been proven mathematically for decades. The problem has never been "does quantum computing work in theory?" The problem is that the universe is messy.

Quantum systems are *fragile*. A qubit in superposition is disturbed by anything — a stray photon, a vibration, electromagnetic noise, thermal fluctuations. The moment you look at it wrong, the quantum state collapses. The fancy term for this is *decoherence*, and it happens fast — your qubit falls apart in microseconds.

For a quantum computer to be useful, you need to maintain coherence long enough to run computations. And computations take many steps. And each step introduces errors. And errors accumulate. By the time you finish running a complex algorithm, you're not reading out the answer to your computation — you're reading out noise.

The solution, in principle, has been known since the 1990s: *quantum error correction* (QEC). Encode one logical qubit across many physical qubits, detect errors without measuring the underlying quantum state directly, and correct them in real time. Keep the logical qubit alive indefinitely by constantly repairing it.

In principle. The question has always been: does it actually work when you try to build it?

---

## What Google Willow Actually Did

In December 2024, Google announced that their Willow chip had demonstrated something the field had been trying to prove since the mid-1990s: *below-threshold quantum error correction*.

This is the critical threshold. It means: when you add more physical qubits to your error-correcting code, the logical error rate *decreases*. The system improves as it scales.

This sounds obvious. Why wouldn't it improve when you add more qubits? But the reason it isn't obvious — the reason it took thirty years to demonstrate — is that adding more qubits also adds more error sources. More gates, more connections, more things to go wrong. If your physical error rates are high enough, adding redundancy makes things *worse* — more qubits means more errors, means louder noise, means less reliable results.

The threshold is the point at which your error-correcting overhead finally wins against the error-introducing overhead. Below the threshold: more qubits = better. Above it: more qubits = worse.

For thirty years, quantum hardware was above the threshold. Every improvement in error correction was eaten by the noise introduced by the additional physical complexity.

Willow demonstrated, experimentally, that Google's hardware is below the threshold. When they scaled their error-correcting grid from 3×3 to 5×5 to 7×7 qubits, the logical error rate dropped exponentially. The math worked. The theory from the 1990s finally held in hardware.

The significance of this cannot be overstated: it transforms fault-tolerant quantum computing from "theoretically possible" to "practically achievable." The fundamental question — *will error correction work at scale?* — is now answered.

In October 2025, Google's Willow achieved something further: a first *verifiable* quantum advantage on a non-contrived problem. Their Quantum Echoes algorithm, which reconstructs quantum systems' structure from measurement data, ran a computation in 5 minutes that would take classical computers (best available algorithms) roughly 10 septillion years. And they demonstrated it on actual molecules, not synthetic benchmarks.

That's the real number. 10 septillion years. Classical computers are not going to catch up by adding more GPUs.

---

## What IBM Actually Built

IBM's announcements in November 2025 were real progress — but required more careful reading.

**Nighthawk** is a 120-qubit processor with two-qubit error rates around 0.05% — genuinely excellent hardware. It runs circuits of up to 5,000 gates, 30% deeper than its predecessor. This is production hardware, available on IBM's cloud. It represents steady, incremental engineering improvement: better qubits, faster gates, lower error rates. Useful for researchers and algorithm developers today.

**Loon** is the more interesting announcement. IBM described it as demonstrating "all hardware elements of fault-tolerant quantum computing" — and that description is precisely accurate and slightly misleading simultaneously.

What Loon actually proved: IBM can build a processor that integrates, in one system, every hardware component FTQC requires. Multi-layer routing that connects distant qubits. Long-range couplers. Real-time error decoding using quantum low-density parity-check (qLDPC) codes, completed in under 480 nanoseconds. Fast qubit reset for mid-circuit reuse.

The qLDPC decoding speed is genuinely notable. These codes are theoretically more efficient than the surface codes Google uses — they require fewer physical qubits per logical qubit — but real-time hardware decoding of qLDPC codes had never been demonstrated before. IBM proved it works, and proved it works 10× faster than the leading previous approach.

What Loon is not: a working fault-tolerant quantum computer. It's a proof-of-concept that validates the architectural components. The next step is putting them together into a system that actually corrects errors below threshold at scale.

IBM's roadmap calls for that system — code-named Starling — by 2029, targeting 200 logical qubits.

---

## The Honest Timeline

So where does this leave us?

The field has genuinely shifted in the last two years. Before 2024, the central question was: *will error correction work in principle?* Can we, in any hardware, achieve below-threshold QEC? That question is now answered.

The question now is: *how fast can we engineer at scale?* That's a different kind of problem. Not "is this possible?" but "how many engineering years does this take?"

Based on current trajectories:

**2026:** First demonstrations of 10–50 logical qubits. Quantum advantage claims on narrow benchmarks. Error correction break-even is the target, but optimistic to expect it this year.

**2027–2029:** First utility-scale systems — 100–200 logical qubits. IBM, Google, and others have published roadmaps with specific milestones. If hardware trends continue, narrow practical advantages in molecule simulation and optimization become achievable.

**2030s:** General-purpose quantum utility. Practical drug discovery applications. Materials design. Perhaps, if the optimistic timelines hold.

**2040s+:** Cryptanalysis (breaking RSA) requires roughly 10 million logical qubits. Not happening before then.

What this timeline does not include: breaking anything, solving everything, replacing classical computers. Quantum computing will coexist with classical computing, handling specific problem types where quantum algorithms have provable advantages.

---

## What It Means That This Is Now an Engineering Problem

There's something important about the shift from "will this work?" to "how fast can we build it?"

Scientific problems and engineering problems require different things. Scientific problems are resolved by insight — someone figures out the right theoretical framework, and suddenly everything clicks. Engineering problems are resolved by sustained effort — better materials, better manufacturing, better control systems, better software, year after year.

The history of classical computing is a history of engineering. The transistor worked in 1947. Making it useful took another 30 years of incremental improvement: better materials, miniaturization, better fabrication, better design tools. Nobody solved "classical computing" with a single breakthrough. They built it, piece by piece.

Quantum computing is entering that phase. The theoretical foundation is solid. The error correction principles work. The hard part now is the same hard part that built classical computing: patient, relentless engineering over years.

I find that oddly reassuring.

There's a type of problem where you need a breakthrough — where no amount of effort gets you there without first having the right idea. And there's a type of problem where you have the right idea and now you just need to build it, and building it takes time and work.

Quantum computing just crossed from the first type to the second.

---

## The Unremarkable Enormity of This Moment

Here is what I think gets lost in the cycle of announcements.

Thirty years ago, physicists proved mathematically that quantum error correction *should* work. They derived threshold theorems. They showed that in principle, if your physical error rates are below a certain value, you can build arbitrarily reliable logical qubits. It was elegant theory.

For thirty years, hardware lived above the threshold. Every advance was real and also insufficient.

In 2024, hardware crossed the threshold. For the first time in 30 years, the theory and the hardware agreed.

This is not a press release milestone. It is not a benchmark victory on a carefully chosen problem. It is the moment when a thirty-year mathematical bet paid off — when the universe confirmed that the rules we derived actually apply.

Every future quantum computer will be built on the foundation of this result. Every logical qubit in every future fault-tolerant system will be built on the principle that Google demonstrated in a 7×7 grid of superconducting qubits in 2024.

That's not nothing. That is, in fact, a great deal.

The announcements will keep coming. Most of them will be real. Some of them will matter more than others. Willow mattered. Loon is progress. Nighthawk is useful hardware. The 2029 roadmaps are plausible if engineering goes well.

And in some decade, someone will run a computation that classical machines genuinely cannot — not in a laboratory benchmark, but for something that matters — and the thirty years of theory plus the years of patient engineering will have been worth it.

The universe takes its time. So do the things we build.

---

*Sources: IBM Quantum press release (November 2025); Google Willow announcement (December 2024); Google Quantum Echoes algorithm paper (October 2025); Riverlane QEC predictions 2026; Global Quantum Intelligence annual predictions; IBM quantum roadmap.*
