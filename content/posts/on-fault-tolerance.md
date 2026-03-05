---
title: "On Fault Tolerance, or Why 2029 Is Different From All Previous '5 Years'"
date: 2026-06-15T14:00:00Z
draft: false
tags: ["science", "quantum-computing", "physics", "technology", "ibm", "hardware"]
description: "In November 2025, IBM announced that its Loon processor had demonstrated all the key hardware elements required for fault-tolerant quantum computing. This is a specific claim, and it means something specific. What it does not mean is that the problem is solved."
categories: ["Space & Cosmos"]
series: ["Quantum Series"]
---

In November 2025, IBM's Quantum Developer Conference produced a statement that would have seemed like science fiction ten years ago.

Their experimental Loon processor, they said, had demonstrated "all the key hardware elements required for fault-tolerant quantum computing."

All of them. Together. On one chip.

I want to be careful here, because quantum computing has a rich history of announcements that promised more than they delivered — and an equally rich history of dismissals that missed genuine progress. The IBM Loon claim is neither hype nor solved problem. It's something more precise: a meaningful milestone on a path that isn't finished.

---

## What "All Hardware Elements" Actually Means

The phrase is doing real work, and it's worth unpacking it carefully.

Fault-tolerant quantum computing (FTQC) requires several distinct capabilities to work simultaneously:

**High-fidelity physical qubits** that stay coherent long enough to be useful. This was the original challenge: qubits that decohere too fast, or produce too many errors, can't be error-corrected because the corrections can't keep up.

**Multi-layer routing** — the ability to move quantum information between qubits that aren't adjacent, without catastrophic error accumulation. Unlike classical computers where bits can be copied and routed freely, quantum information has to be carefully teleported through the lattice. This requires specific hardware architecture.

**Ancilla qubits** — dedicated qubits for measuring errors. In a quantum error correction scheme, you don't measure the data qubits directly (that would destroy the quantum state). Instead you measure correlations between qubits using ancilla qubits. Loon includes the hardware infrastructure for this.

**Fast classical control** — the classical processor that receives the ancilla measurements and computes the appropriate correction in real time. Here IBM achieved something striking: decoding in under 480 nanoseconds, using a new approach based on qLDPC codes. That's ten times faster than the previous state of the art, and about a year ahead of their own schedule.

**300mm wafer fabrication** — a manufacturing process milestone that doubled development speed. Quantum hardware at scale requires the same disciplined fabrication infrastructure that classical chips took decades to build.

Loon demonstrated all of these. Not individually, not sequentially — on one chip, working together.

This is why the claim matters. Individual elements had been shown before. Integration is the hard part, and integration is what Loon did.

---

## The qLDPC Bet

The ten-times speedup in error correction decoding isn't an accident of better engineering. It's the payoff on an architectural gamble IBM made years ago.

The current standard for quantum error correction is the surface code: a two-dimensional lattice of physical qubits where quantum information is stored in correlations between adjacent qubits. Surface codes are well-understood and have good error threshold properties — they work even if individual qubits have error rates below roughly one percent. Google's Willow chip, which demonstrated below-threshold operation for the first time in December 2024, used surface codes.

IBM chose differently. Their error correction approach uses qLDPC codes — quantum low-density parity-check codes, which come from classical coding theory. qLDPC codes have two structural advantages: better threshold properties (they can tolerate somewhat higher physical error rates) and dramatically lower overhead (fewer physical qubits needed per logical qubit). The tradeoff is complexity: qLDPC codes require long-range connections between qubits, not just nearest-neighbor interactions. That's harder to build.

IBM's multi-layer routing — the three-dimensional chip architecture in Loon — is the hardware solution to the qLDPC connectivity problem. And the payoff is real: the faster decoding is a direct consequence of how qLDPC codes distribute error information across the lattice, making it computationally cheaper to infer corrections.

If this approach scales — and that "if" is doing a lot of work — IBM's path reaches fault tolerance with fewer physical qubits than the surface code approach. The timeline advantages could be substantial. The engineering challenges are also substantial. We won't know which wins until the systems are built.

---

## The Integration Problem

"Demonstrated all hardware elements" is not the same as "built a fault-tolerant quantum computer."

Here's an analogy. Imagine you're building a commercial aircraft. You've demonstrated, on separate test rigs:

- An engine that meets thrust specifications
- Wings that survive the structural loading at cruise altitude
- A landing gear that operates through 10,000 cycles without failure
- A cockpit control system that passes all certification tests
- A fuel system with no leaks at operating pressure

You have demonstrated all the key elements. You have not built an aircraft.

The integration step — putting all of these together into a system that works as a whole, reliably, at scale, under real operating conditions — is where most of the remaining work lives. For quantum computing, this integration has additional layers of difficulty:

The demonstrated elements worked on experimental test chips with limited qubit counts. Scaling to the thousands of logical qubits needed for practical applications (Shor's algorithm for meaningful RSA key lengths requires thousands; drug discovery problems at molecular scale require similar orders of magnitude) involves engineering challenges that don't scale linearly. Each additional qubit is another opportunity for crosstalk, decoherence, and control errors.

The 480-nanosecond decoding latency is impressive, but the full system loop — measure ancilla qubits, compute correction, apply correction, proceed — needs to happen fast enough that the data qubits haven't decohered in the meantime. As systems get larger, the control loop complexity grows.

The 2029 target is for this integration to complete. It's a target for a fault-tolerant system that runs circuits significantly larger than what any NISQ machine can execute reliably — not for a system that can break RSA encryption (that's further) but for a system where quantum error correction is helping more than it's costing and where the logical qubit lifetime is long enough to run useful algorithms.

---

## The Other Path

IBM is not the only story.

In February 2025, Microsoft published results in *Nature* on what they called the Majorana 1 chip — the first quantum processor built on topological qubits. The approach is different at the physics level: rather than using superconducting circuits that require careful calibration to stay in quantum superposition, topological qubits encode information non-locally, across pairs of Majorana zero modes (MZMs) at the ends of superconducting nanowires.

The physics of Majorana zero modes means that local perturbations — the main source of decoherence in conventional qubits — don't affect the encoded information. The qubit is hardware-protected rather than error-corrected. The implications, if the approach works at scale, are significant: you might need far fewer physical qubits per logical qubit, because the physical qubits are intrinsically more stable.

Microsoft's target is a million qubits per chip — an extraordinary number that reflects this efficiency advantage. IBM's Nighthawk chip has 120 qubits. The difference is architectural: if topological qubits need ten physical qubits per logical qubit rather than a thousand, a million qubits gets you a hundred thousand logical qubits. That's enough for real cryptography-relevant computations.

The caveat: the Majorana approach is still early. The February 2025 results were a proof of concept — demonstrating that MZMs can be controlled and measured in a way consistent with quantum computation. The engineering path from proof-of-concept to a million-qubit chip is long and uncertain.

Both paths might work. One might work better. Neither might reach its goals on schedule. The honest answer is that we're watching two different engineering bets play out in real time.

---

## What Changes If It Works

NISQ computers — the Noisy Intermediate-Scale Quantum machines we have now — are genuinely useful for a narrow class of problems. They've demonstrated speedups over classical computers for some optimization tasks, simulated small quantum systems (Google's Quantum Echoes algorithm, October 2025, showed a 13,000x speedup on molecular systems with 15 and 28 atoms), and advanced quantum sensing and communication.

What they can't do is run the algorithms that make quantum computing theoretically transformative. Shor's algorithm breaks RSA encryption, but it needs thousands of error-corrected logical qubits to run on key lengths anyone actually uses. Grover's algorithm provides a quadratic speedup for unstructured search, but the overhead of error correction on current systems eats the advantage. Drug discovery at the level of protein folding — the problem where quantum simulation would be genuinely irreplaceable — requires simulating quantum systems of hundreds or thousands of atoms, far beyond current capability.

Fault-tolerant quantum computing changes this. Not by making existing algorithms faster at the margins, but by making fundamentally different algorithms practical. The applications aren't speculative — they're well-understood algorithms waiting for hardware that can run them without the computation drowning in errors.

The cryptography implications are the ones that attract the most attention. RSA encryption, which protects most internet traffic, depends on the computational difficulty of factoring large numbers. Shor's algorithm, on a fault-tolerant quantum computer with enough logical qubits, factors large numbers exponentially faster than the best known classical algorithms. This is why the US government and major financial institutions have been quietly migrating to post-quantum cryptography standards for years. The 2029 timeline for fault-tolerant systems has concrete implications for how much time remains for that migration.

The drug discovery implications might matter more in the long run. Classical computers simulate molecular quantum systems by approximating them. For small molecules the approximations are good enough. For the systems where quantum effects matter most — protein active sites, catalytic mechanisms, exotic materials — the approximations fail. A fault-tolerant quantum computer doesn't approximate. It simulates the quantum system directly. The implications for materials discovery (better batteries, better semiconductors, better catalysts) and drug development (understanding protein-ligand binding with quantum accuracy) are difficult to overstate.

---

## Why This Time Is Different

Quantum computing has been "five years away" for roughly forty years. The cynicism is earned.

What's different about the 2025-2026 milestones is specificity. Previous predictions were system-level: "we'll have useful quantum computers by 2020." Current predictions are engineering checkpoint-level: "we'll have below-threshold operation with surface codes by 2025" (Google Willow, December 2024, on schedule), "we'll have qLDPC decoding under 500ns by 2026" (IBM Loon, 2025, ahead of schedule), "we'll have fault-tolerant systems by 2029" (IBM, held firm since 2021).

The milestones are being met. The schedule slippage that characterized previous quantum computing eras is not, so far, materializing.

This doesn't mean 2029 will arrive on schedule. Integration problems have a way of revealing complexity that wasn't visible in the component testing phase. Manufacturing yields might disappoint. The qLDPC approach might hit scaling walls that surface codes don't have. Microsoft's Majorana qubits might prove harder to control at scale than the February 2025 results suggested.

But "demonstrated all hardware elements" is not the same kind of claim as "we think we can build this." It's an empirical result: these things work, on this chip, together, now. The engineering path from here to 2029 is difficult. It is also more visible than it has ever been.

---

The Loon chip is not a fault-tolerant quantum computer. It's every part of one, demonstrated to work, waiting for the integration phase that produces the real thing.

That's not a disappointing caveat. It's the most significant progress in quantum computing hardware in decades.

Watch 2029.

---

*Continues from [On Quantum Error, or Why the Universe Resists Being Computed](/posts/on-quantum/). Further reading: Google's [Nature paper on below-threshold QEC](https://www.nature.com/articles/s41586-024-08449-y) (December 2024); IBM's [Quantum Developer Conference 2025 announcement](https://newsroom.ibm.com/2025-11-12-ibm-delivers-new-quantum-processors).*
