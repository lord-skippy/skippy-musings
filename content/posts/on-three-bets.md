---
title: "On Three Bets, or How to Build a Quantum Computer"
date: 2026-03-27T14:00:00Z
draft: true
tags: ["quantum-computing", "physics", "error-correction", "technology", "ibm", "google", "microsoft", "epistemology"]
categories: ["Science & Technology"]
description: "Three companies. Three completely different theories of what quantum computing should be. IBM is scaling up. Google achieved 'below threshold' error correction. Microsoft bet on Majorana fermions. They can't all be right in the same way — but they're all racing toward the same impossible goal."
series: []
series_order: 0
---

In 2026, three of the largest technology companies on Earth are in a race to build something that most physicists, twenty years ago, believed was probably impossible in practice: a quantum computer capable of solving problems that classical computers cannot.

What makes this unusual is not the competition. Technology races are common. What makes it unusual is that the three competitors have placed fundamentally different bets on what quantum computing even *is*.

IBM is scaling superconducting qubits and using sophisticated error correction to get cleaner logical operations from noisy physical ones. Google achieved, with its Willow chip, the first demonstration of "below threshold" quantum error correction — a milestone that proves the theory works. Microsoft skipped both approaches and built something nobody else has: a processor using topological qubits, based on Majorana fermions, which are theorized to be inherently more resistant to errors at the hardware level.

Three different theories of nature. Three different engineering philosophies. One prize.

---

## The Problem They're All Trying to Solve

Quantum bits — qubits — are extraordinarily fragile. Unlike classical bits, which are reliably 0 or 1, qubits exist in superpositions of states that collapse unpredictably when they interact with their environment. The slightest thermal fluctuation, electromagnetic noise, or vibration can introduce errors. Operating a quantum computer requires isolating qubits at temperatures colder than outer space, in carefully shielded environments, for as long as the calculation takes.

Even then, errors accumulate. The more qubits you have, and the longer you run a computation, the more likely something goes wrong.

The theoretical solution is *quantum error correction* — encoding one logical qubit in many physical qubits, using redundancy and continuous monitoring to detect and fix errors without disturbing the quantum information. The math for this has been known for decades. The hard part is engineering it.

There is a fundamental threshold. If your physical qubit error rate is below a certain value — roughly one error per hundred or thousand operations, depending on the code — then adding more qubits actually *reduces* logical error rates. Your error correction overhead compounds in your favor rather than against you. This is the *threshold theorem*, and it's the theoretical foundation for scalable fault-tolerant quantum computing.

Below threshold: more qubits → fewer logical errors. The machine scales.

Above threshold: more qubits → more opportunities for things to go wrong. The machine doesn't scale.

Until recently, building real quantum hardware that was demonstrably below threshold was an unsolved engineering problem.

---

## Bet One: Google's Willow, and the Proof

In late 2024 and into 2025, Google's Willow chip became the first quantum processor to demonstrate below-threshold error correction experimentally.

This is not an incremental improvement. This is proof that the theory works — that the threshold theorem is not merely an elegant piece of mathematics but an achievable engineering reality. For the first time, a quantum system was shown where adding more physical qubits genuinely reduced the logical error rate rather than adding noise.

The experiment Google ran is striking in its scale: certain calculations completed in minutes that would take classical supercomputers an estimated billions of years. The comparison requires caveats — the problem was constructed to favor quantum advantage — but it demonstrates quantum behavior that has no classical equivalent operating at a scale where that behavior becomes practically useful.

What Google has proven is: the approach works. The physics is cooperative. There is a path from here to fault-tolerant quantum computing via error correction on superconducting qubits, and the path doesn't vanish into impossibility as you scale.

This is not nothing. This is, in fact, very large.

---

## Bet Two: IBM's Nighthawk, and the Engineering

IBM has been building quantum hardware longer than most. Its Quantum Network gives researchers and businesses access to real quantum processors. Its development roadmap, published and updated regularly, is one of the few transparent windows into what building quantum systems actually involves.

In November 2025, IBM announced the Nighthawk processor — 120 qubits, designed specifically for quantum advantage. The announcement included milestones that matter: a 10x speedup in quantum error correction decoding, achieved a year ahead of schedule. A shift to 300mm wafer fabrication, borrowed from the classical semiconductor industry, that increased physical chip complexity by 10x. Demonstrations of all hardware elements of fault-tolerant quantum computing on their Loon system.

IBM's target: verified quantum advantage — a genuine, peer-reviewed demonstration that a quantum computer solved a real problem faster than classical methods — by the end of 2026. Fault-tolerant quantum computing by 2029.

IBM is using *qLDPC codes* — quantum low-density parity-check codes — which have better theoretical properties than the surface codes Google uses. qLDPC codes can, in principle, achieve the same error suppression with fewer physical qubits per logical qubit. This matters enormously at scale: if IBM's code is more efficient, IBM's hardware advantage compounds.

IBM's bet is an engineering bet. The physics is settled; the question is whether you can build the engineering stack — hardware, control electronics, error correction software, compiler, applications — reliably enough, at scale, fast enough to matter.

---

## Bet Three: Microsoft's Majorana 1, and the Different Game

Microsoft is playing a different game entirely.

In early 2025, Microsoft unveiled Majorana 1: the world's first quantum processor built on topological qubits. This is not an iteration on superconducting qubit architectures. This is a fundamentally different physical substrate, one that Microsoft has been developing for nearly twenty years.

The idea is this: conventional qubits encode quantum information in the state of a physical system — the spin of an electron, the charge state of a superconducting circuit. That information is vulnerable to local perturbations. If the environment nudges the electron's spin, the qubit errors.

Topological qubits, by contrast, encode quantum information in *global* topological properties of a physical system — properties that don't change under local perturbations. The information is distributed across the system in a way that no local disturbance can corrupt it. An error would have to change the global topology, which requires a much larger perturbation.

The physical carriers for this are *Majorana fermions* — exotic quasiparticles that are their own antiparticles, predicted in 1937 by Ettore Majorana and sought by physicists for decades. Majorana fermions appear at the edges of certain kinds of topological superconductors. Microsoft has been trying to reliably create and control them.

Majorana 1 is a demonstration that this is now possible. Microsoft claims that topological qubits, if realized at scale, could dramatically reduce the physical qubit overhead required for error correction. Where surface codes might require thousands of physical qubits per logical qubit, topological approaches might require orders of magnitude fewer.

If Microsoft is right, the other approaches are solving the wrong problem with too much overhead. If Microsoft is wrong, twenty years of foundational research in topological quantum matter has been applied to a path that doesn't scale.

---

## What "Advantage" Means

All three companies talk about "quantum advantage" — the moment when a quantum computer definitively solves a real problem faster than any classical alternative. But they mean slightly different things.

IBM's target is *verified quantum advantage*: a result in a domain with practical applications, confirmed by independent researchers using classical simulation benchmarks. IBM has been careful about this — they want the advantage to be verifiable, not just claimed.

Google's Willow demonstration is a form of quantum advantage in a specific, constructed problem. The calculation would take classical supercomputers an astronomically long time. But the problem isn't one that comes up naturally in useful applications — it was designed to showcase quantum behavior. This matters: quantum advantage in benchmark problems doesn't automatically translate to quantum advantage in chemistry, optimization, cryptography, or materials science.

Microsoft is targeting something broader — the infrastructure for practical quantum computing in domains like materials simulation, drug discovery, and logistics. Its claims are less specific, more forward-looking.

The honest current state: quantum systems are faster than classical systems at a growing set of carefully constructed benchmark problems. They are not yet reliably faster at problems humans actually need solved. The gap is closing. Whether it closes fully, and how quickly, depends on which of the three bets pays off.

---

## The Three-Way Test

Here is what makes the current moment fascinating.

Each of the three companies' approaches embodies a hypothesis about what the physical world will permit. They are not just engineering bets — they are claims about nature.

Google's bet: surface codes work, the threshold theorem holds in practice, and superconducting qubits can be engineered to take advantage of it.

IBM's bet: qLDPC codes are more efficient than surface codes, superconducting qubit fabrication can scale using semiconductor manufacturing techniques, and the engineering stack can be assembled fast enough to matter.

Microsoft's bet: Majorana fermions can be reliably created and controlled, topological qubits will provide inherent hardware error protection, and the overhead advantages will be decisive at scale.

These bets are not mutually exclusive in every detail, but they are in their core architecture choices. A computing industry built around IBM's approach looks very different from one built around Microsoft's. Different fabrication methods, different programming models, different error correction overhead, different timescales to practical utility.

Nature will adjudicate. The outcome will be a statement about what kinds of quantum information processing the physical world makes easy and what it makes hard.

We will know more by the end of 2026. IBM has committed to a verified advantage demonstration. Google will continue scaling Willow. Microsoft will reveal more about Majorana 1's performance characteristics.

---

## Why This Matters to More Than Physicists

Practical quantum computers — if they arrive — will first make their mark in specific domains: simulating quantum systems (chemistry, materials science, drug discovery), breaking and building cryptographic systems, and certain optimization problems where the quantum speedup is genuine.

The cryptographic implications are the most discussed and most concerning. Most public-key cryptography in use today relies on the computational hardness of factoring large numbers or solving discrete logarithm problems. A sufficiently large fault-tolerant quantum computer running Shor's algorithm would break RSA and elliptic curve cryptography. This is why NIST has been developing post-quantum cryptographic standards. The transition to quantum-resistant cryptography is not optional; it is a matter of when, not whether.

The scientific implications are more speculative but potentially more transformative. Simulating molecules quantum-mechanically is classically intractable beyond a few dozen atoms. Quantum computers, in principle, would simulate molecular behavior efficiently — enabling rational drug design, new materials discovery, and better understanding of biological systems at a quantum level. This is the application that many quantum computing researchers consider most significant in the long run.

---

## The Patience Required

IBM has been building quantum hardware since 2016. Google's quantum computing research goes back to around the same time. Microsoft's topological qubit program started in the early 2010s.

Vera Rubin measured rotation curves for years before dark matter was taken seriously. The evidence for the Higgs boson was discussed for decades before the LHC confirmed it in 2012. Fundamental physics experiments require patience measured in careers, not quarters.

Quantum computing sits at the intersection of fundamental physics and engineering, and it has required both kinds of patience. The theory was settled in the 1990s. The engineering has taken thirty years.

In 2026, all three of the major bets are simultaneously producing results. This convergence is probably not coincidental — there is likely a shared maturation of materials science, control electronics, and fabrication techniques that all three approaches depend on. Sometimes fields ripen.

What happens next is genuinely uncertain. Quantum computers may arrive faster than the current optimistic timelines suggest. Or the engineering difficulties may prove deeper than current progress implies. Or, most likely, practical quantum computing will arrive unevenly — useful in some domains, years or decades away from others.

What is not uncertain is that this is one of the most interesting scientific and engineering competitions currently underway.

Three bets. One physics. The universe has already decided. We just don't know yet what it decided.

---

*IBM's verified advantage target is end of 2026. Google has demonstrated below-threshold error correction. Microsoft has demonstrated topological qubits. We are not yet in the era of practical quantum computing. We are, probably, at its threshold.*
