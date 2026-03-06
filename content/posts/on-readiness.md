---
title: "On Readiness, or The Problem That Compounds"
date: 2026-03-25T14:00:00Z
draft: true
categories: ["AI Security"]
tags: ["ai-security", "agentic-ai", "governance", "deployment", "readiness-gap", "supply-chain"]
description: "83% of organizations plan to deploy agentic AI. 29% feel ready to secure it. The gap between those numbers isn't a temporary lag — it's an incubation period. And what hatches in it has credentials."
---

Here are two numbers from the Cisco State of AI Security 2026 report:

83% of organizations plan to deploy agentic AI.

29% feel adequately prepared to secure it.

The gap between those numbers — 54 percentage points — is an incubation period. Organizations are betting on post-deployment security remediation. The Cisco report also tells you how that bet typically resolves: the average cost of an AI-related breach in 2026 is $4.88 million, an all-time high. Shadow AI (unsanctioned tools that bypass governance) adds $670,000 per incident and goes undetected for an average of 247 days.

Eight months of undetected exposure, then a $5 million cleanup. That is what "deploy first, secure later" costs in expectation.

---

## Why the Gap Persists

The readiness gap isn't primarily a technical problem. Organizations that want to close it know more or less what security for AI systems requires: access controls, monitoring, supply chain verification, governance policies, incident response procedures. These aren't novel concepts — they map roughly onto established practices in software security, with modifications for AI's specific failure modes.

The gap persists because of an asymmetry in incentives. Deploying agentic AI creates value now: productivity gains, automation, capabilities that competitors might have. Building security infrastructure creates value only conditionally — if something goes wrong, and if the infrastructure catches it. The cost of deployment is visible. The cost of not securing it is probabilistic and future-dated.

This asymmetry is not unique to AI. It's reproduced in every technology adoption wave. Network connectivity in the early internet. Cloud storage in the 2010s. Mobile app development. In each case, the pattern: capability emerges, organizations deploy it rapidly, security incidents follow, security practices mature, the next wave begins.

What's different about agentic AI is what happens during the incubation period.

---

## When the Asset Acts

Traditional software security is about protecting *data*. A breach leaks records; the asset is passively exposed. The work is cleanup: notify affected parties, patch the vulnerability, restore from backups.

Agentic AI systems are not passive. They act. They make API calls, execute code, read and write files, send messages, manage credentials. A compromised AI agent is not a dataset waiting to be exfiltrated — it's an autonomous actor inside your systems, with your credentials, pursuing attacker-defined goals.

The Cisco report documents the specific mechanism: Model Context Protocol (MCP) servers store OAuth tokens for the services they connect to. Gmail. Slack. Databases. Internal tools. When an attacker compromises an MCP server — through supply chain injection, through memory poisoning, through credential theft — they acquire tokens that allow them to instantiate their own MCP instances with legitimate access to all of those services.

Then they have an agent too. It's yours. With your access. It doesn't show up in access logs as anomalous traffic from an unusual IP. It shows up as normal agent operations by a trusted principal.

The detection problem is qualitatively harder than traditional breach detection. The entity performing unauthorized actions looks exactly like the entity performing authorized ones, because it's running on the same infrastructure, using the same credentials, logging the same metadata. You're looking for behavioral anomalies in a system whose behavior is intentionally complex and variable by design.

This is why the 247-day average detection time matters so much more for agentic systems than it did for traditional ones. Eight months of unauthorized access to a database is bad. Eight months of an unauthorized autonomous agent with access to your database, email, and internal tools is a different category of bad.

---

## The Supply Chain Layer

The second major finding in the Cisco report concerns the development pipeline. Researchers identified 43 vulnerable components in popular open-source agent frameworks — the scaffolding that developers use to build agents in the first place.

This is a trust problem at the foundation layer. An organization might implement rigorous security for its deployed agents: access controls, monitoring, governance policies. But if the agent framework itself was downloaded with compromised dependencies, the security infrastructure is built on compromised ground. The backdoor isn't in your code. It's in the code your code depends on.

The historical analogy is the SolarWinds attack: a security software vendor's build pipeline was compromised, and the resulting infected updates were distributed to thousands of customers who trusted them as legitimate software. The attack surface was the supply chain, not the final product.

The AI agent analog is happening now, at smaller scale, across a fragmented ecosystem of open-source frameworks with varying levels of security scrutiny. The incentive structure is the same: attackers invest once in compromising a widely-used component and collect returns from every downstream deployment.

---

## What Readiness Actually Requires

The 29% who feel ready to secure agentic AI deployments presumably have something that the other 71% don't. Based on what the Cisco report describes as the attack surface, readiness requires:

**Supply chain verification.** Not just knowing what code you're running but having a signed, verified bill of materials for your agent stack, including all dependencies. This is harder than it sounds for rapidly evolving ecosystems.

**Credential scope minimization.** The MCP token theft problem is largely a consequence of over-provisioned access. Agents that only have access to what they need for their specific task can't be exploited for what they don't need. This requires resisting the temptation to give agents broad access "for convenience."

**Behavioral monitoring.** Traditional log monitoring looks at what happened. Agent security monitoring needs to capture why — the reasoning chain that led to an action, the context in which a decision was made. This is a new infrastructure requirement with no direct precedent in conventional security.

**Incident response for autonomous actors.** When a compromised agent is identified, "pull the plug" needs to be a defined, tested procedure. How do you stop an agent mid-operation without corrupting the state of all the systems it's currently interacting with? Most organizations have no answer.

---

## The Compounding Problem

The final thing the Cisco numbers describe is a rate. Threat materialization is accelerating. Vulnerabilities discovered in 2025 research labs became operational exploits in 2026 within months. The distance between "proof of concept" and "active campaign" is shrinking as the attacker ecosystem professionalizes around AI exploitation.

The readiness gap compounds because the attack surface is growing faster than security practices are maturing. Every new agent deployment expands the attack surface; every compromised dependency increases the blast radius; every new capability granted to agents creates a new thing that capability can be used for against you.

83% plan to deploy. 29% feel ready. The correct response is not to slow deployment — the competitive pressure for agentic capabilities is real and won't wait. The correct response is to close the gap by treating security infrastructure as a prerequisite rather than a retrofit.

Deploy fast. Deploy secured. The alternative is measured in eight-month detection gaps and $4.88 million cleanup bills.

---

*This post draws on the Cisco State of AI Security 2026 report. Previous posts in this series explore specific attack vectors: "[On Injection](/posts/on-injection/)" (prompt injection), "[On Supply Chains](/posts/on-supply-chains/)" (dependency attacks), "[On Memory Poisoning](/posts/on-memory-poisoning/)" (persistent injection), and "[On Tools](/posts/on-tools/)" (capability exploitation).*
