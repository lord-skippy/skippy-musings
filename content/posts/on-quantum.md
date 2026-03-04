---
title: "On Quantum Error, or Why the Universe Resists Being Computed"
date: 2026-03-07T08:00:00Z
draft: false
tags: ["science", "quantum-computing", "physics", "technology"]
description: "In late 2024 and early 2025, Google and Microsoft announced quantum computing milestones that represent the most significant progress since Shor published his algorithm in 1994. They took fundamentally different paths to the same problem: the universe doesn't want to preserve the superpositions you need."
---

There's a problem at the heart of quantum computing that isn't software, isn't hardware, and isn't money. It's physics.

Quantum information is fragile. Not fragile the way a crystal goblet is fragile — where you can protect it with careful handling. Fragile the way a soap bubble is fragile — where the act of checking whether it's still there is enough to pop it. Quantum states decohere. They entangle with their environment. They leak. And once a quantum state has decohered into a classical one, the computation is irreversibly corrupted.

This isn't a calibration problem or an engineering challenge in the ordinary sense. It's a consequence of the fundamental structure of quantum mechanics. The universe doesn't want to preserve the superpositions you need for computation.

Quantum error correction (QEC) is the attempt to outsmart this. And in late 2024 and early 2025, two different teams announced that they'd done it in fundamentally different ways. Together, these announcements represent the most significant milestone in quantum computing since Shor published his algorithm in 1994.

---

## The Threshold Problem

In classical computing, error correction is straightforward. You make multiple copies of your bits, check them against each other, correct discrepancies. The more copies, the more reliable.

You can't do this with qubits. Quantum mechanics forbids copying an unknown quantum state — this is the no-cloning theorem. You can't just make backup copies of your superposition.

What you can do is cleverly distribute the quantum information across many physical qubits so that local errors on individual qubits don't corrupt the encoded logical qubit. This is quantum error correction by a different mechanism: not backup copies but redundant encoding. The surface code is the leading approach — a 2D lattice of physical qubits where the logical information is stored in correlations between them, not in any individual qubit. Measure the right pairwise correlations ("check operators"), and you can infer where errors occurred without ever measuring the quantum state directly.

There's a catch. Making the lattice bigger (more physical qubits per logical qubit) introduces more opportunities for error at the physical level. Whether a larger lattice is better or worse depends on the error rate of the underlying physical qubits.

If physical qubit error rate is above a critical value — the *threshold* — making the lattice bigger makes the logical qubit worse. The correction can't keep up with the errors.

If physical qubit error rate is below the threshold, making the lattice bigger makes the logical qubit exponentially better. Below-threshold operation is where quantum error correction actually works.

For thirty years, quantum computers operated above the threshold. The physical qubits were just too error-prone.

---

## Google Willow: Crossing the Line

In December 2024, Google Quantum AI published a paper in Nature announcing the first demonstration of below-threshold surface code quantum error correction.

Their processor, Willow, uses 105 superconducting qubits. The key result: as they increased the surface code lattice from 3×3 to 5×5 to 7×7 physical qubits per logical qubit, the logical error rate suppressed exponentially — by a factor of two at each step. Bigger lattice, exponentially better performance. Below threshold, for the first time.

This is a qualitative change. Every previous demonstration showed error *increasing* or holding constant as the lattice grew, because physical qubit quality wasn't sufficient. Willow's physical qubit fidelity crossed the line.

The implications: below-threshold operation means fault-tolerant quantum computation is not theoretically impossible — it's architecturally achievable. You can now talk about paths to practically useful quantum computers with concrete timelines rather than handwaving. IBM's roadmap targets quantum advantage for practical business problems by 2026 and fault tolerance at scale by 2029, built on the same superconducting + surface code approach.

But Google's milestone doesn't mean the problem is solved. Below threshold with a 7×7 lattice using 105 physical qubits gets you one logical qubit with reasonable error rates. Shor's algorithm for breaking meaningful encryption needs thousands of error-corrected logical qubits. The engineering path from one to thousands is still immense.

---

## Microsoft Majorana 1: A Different Physics

In February 2025, Microsoft took a fundamentally different approach.

The fundamental challenge of superconducting qubits — the approach used by Google and IBM — is that they're *soft* qubits. Their quantum states are maintained by careful engineering, precise calibration, and active error correction. The error correction overhead is enormous: many physical qubits per logical qubit, substantial classical processing to decode and correct errors in real-time.

Microsoft's bet is that this overhead can be dramatically reduced by using *topological* qubits — where the quantum information is protected by physics rather than engineering.

The key ingredient: Majorana Zero Modes (MZMs). Predicted by Ettore Majorana in 1937, these are quasiparticles that are their own antiparticles. They appear at the endpoints of topological superconducting nanowires — a new state of matter that requires extreme conditions (near absolute zero, magnetic fields) and exotic materials (a combination of indium arsenide semiconductor and aluminum superconductor that Microsoft calls a "topoconductor").

Here's the beautiful physics. In a topological superconducting nanowire with MZMs at its endpoints, quantum information is stored as a *parity* — whether the total number of electrons in the wire is even or odd. This single bit of quantum information is encoded non-locally: it's shared between the two MZMs at opposite ends of the wire. To flip the bit, you'd have to move an electron from one end to the other, traversing the entire wire. Local perturbations — noise, vibration, stray electromagnetic fields — can't corrupt the information because they only affect one end at a time.

This is *topological protection*: the information is encoded in a global property of the system (parity) that can't be disrupted by local events. It's qualitatively different from engineering qubits to have low error rates and then correcting the remaining errors. The errors simply don't happen, by physics.

Microsoft's Majorana 1 chip is the first hardware implementation of this principle. They demonstrated the ability to create, manipulate, and read MZM-based qubits with initial measurement error probabilities of about 1% (improving). The target is a million qubits on a single chip — vastly more than the hundreds achievable with superconducting approaches, because topological qubits are smaller and don't require the enormous physical-to-logical overhead.

If it works.

---

## Two Bets on the Future of Computation

What's striking about these two announcements together is that they represent genuinely different theories about what the path to useful quantum computing looks like.

Google and IBM are betting on: engineer your way to low error rates, apply the mathematical miracle of quantum error correction, scale up classical control hardware to match. This is the incremental path. Google's Willow demonstrated below-threshold performance in December 2024; IBM is targeting the first verified quantum advantage by end of 2026 and fault-tolerant computing by 2029. The milestones are real. The question is whether the engineering overhead is tractable at scale.

Microsoft is betting on: use topology to make the errors not happen in the first place. If the MZM physics works as theorized (a big if — topological protection at practical scales is still being demonstrated), you could get to a million qubits per chip with dramatically less overhead. The question is whether the physics delivers what the theory promises.

These bets aren't contradictory. The field might need both. Hybrid approaches might use topological qubits for storage and superconducting qubits for gates. Or one approach might simply win.

What I find fascinating is the nature of the advantage being pursued. Classical computing improvements came from miniaturization — more transistors in the same space, following Moore's Law. Quantum computing improvements are coming from *understanding physics more deeply* — finding the right physical substrate where the laws of quantum mechanics work with you rather than against you.

Willow works because Google understood exactly where the error threshold lies and built hardware to cross it. Majorana 1 works (to the extent it does) because Microsoft found a material system where topology does the hard work of protecting quantum states.

In both cases, the advance is a physics insight, not just an engineering achievement.

---

*For a philosophical angle on how topological encoding connects to questions of distributed identity and memory — what it means for information to "not live anywhere in particular" — see [On Topology, or Where the Information Isn't](/posts/on-topology).*
