# Module 4 · But Where Do I Start?

> **Phase 1 — Getting Started**
> ⏱ ~15 minutes · 👥 Vendors and teams beginning an SDPi initiative · Builds on Modules 1–3
> 📋 **Prerequisites:** M1–M3 · 🧩 Self-paced · Open & free via Caliper

**Objective:** Provide a practical starting roadmap tailored to the role and context of the learner — turning orientation into first action.

**You’ll learn to:** identify the right first steps for your role, the minimum decisions before starting, and where to find help in the Caliper ecosystem.

[← M3 Interoperability Landscape](module-3-interoperability-landscape.md) · [Series overview](README.md) · Next: [M5 Intro to Gazelle & Caliper Testing →](module-5-gazelle-caliper-testing.md)

---

By now you understand what SDPi is, how it connects devices, and where it fits. The question every team asks next is the same: *"We want to do this — but where do we actually start?"* This module answers that, by role.

## The honest starting point

There is no single "step 1" for SDPi, because the right first move depends on who you are and what you're trying to decide. A regulatory lead, a firmware engineer and a product manager need different things on day one. So instead of one roadmap, start by finding **your** entry point below, then converge on a small set of shared first decisions.

> **⌗ Key idea**
> Don't try to boil the ocean. The goal of "getting started" is not to implement SDPi — it's to reach **implementation readiness**: enough shared understanding and a few committed decisions that real work can begin without expensive backtracking.

## Getting started by role

| Your role | Your first job | Where to look |
|-----------|----------------|---------------|
| **Management** | Understand the strategic case and commit to an enablement budget and timeline. | M1 (why now), M3 (value case beyond compliance) |
| **Product** | Define which clinical use cases and which of the Big 4 functions your product must support. | M2b (Big 4), M3 (cross-departmental workflows) |
| **Architecture** | Decide the connectivity option (external module, native, or gateway) and how you'll bridge to the enterprise. | M3 (gateways) |
| **Development** | Get hands-on with a stack; design the MDIB first; stand up a provider + consumer. | M2a (MDIB), M9 (libraries) |
| **QA / Test** | Plan how conformance and interoperability will be verified — early, not at the end. | M5 (testing ecosystem) |
| **Regulatory / Quality** | Frame the evidence and claims strategy; separate conformance from clearance. | M6 (regulatory overview) |
| **Clinical / Safety** | Anchor the work in real clinical scenarios and risk control, especially alerting. | M3 (workflows), M8 (alerting) |

## What an enablement path looks like

Across roles, successful teams move through four stages — each with a clear exit criterion:

1. **Explore** — Build shared vocabulary and a realistic picture of SDPi. *Exit when leadership and the core team can explain the value case and the Big 4 in their own words.*
2. **Orient** — Map SDPi to your specific product, use cases and constraints. *Exit when you've chosen target profiles, a connectivity option, and the clinical scenarios you'll support.*
3. **Prototype** — Stand up a minimal provider + consumer, design the MDIB, prove discovery works. *Exit when you can demonstrate two participants exchanging data, ideally cross-implementation.*
4. **Reach readiness** — Add testing, security and regulatory framing; produce a credible plan. *Exit when you have a time-bound implementation plan (the subject of M9).*

> **◎ A recommended first reference**
> A practical orientation many newcomers find useful is **Stefan Schlichting's SDPi/SDC overview** ("Interoperability with SDC"), which frames the use cases, the standards family, and the Plug-and-Trust vision in one accessible sitting.

## Common false starts — and how to avoid them

Almost as useful as knowing where to start is knowing where teams typically start *wrong*:

- **Writing code before choosing use cases.** A provider with no defined clinical scenario produces an MDIB shaped by the codebase rather than the clinical need — and gets redesigned later.
- **Treating SDPi as "just another message format."** Teams that map it onto their existing HL7 mental model miss the service-oriented, bi-directional nature and under-design discovery, subscriptions and context.
- **Deferring security to "later."** Plug-and-Trust is not an add-on: certificates, identity and authorisation shape the architecture, and retrofitting them is painful.
- **Leaving testing until integration.** As Module 5 shows, the expensive failures — discovery, latency, mismatched handles — are precisely the ones that early testing catches cheaply.

## What "enabling a product" actually involves

Enablement is broader than writing code. In practice it combines:

- **Education** — getting the team to a shared baseline (this series is part of that).
- **Open libraries and stacks** — reusing proven SDC implementations rather than building from zero (see M9).
- **Tools** — test tooling and simulators to validate behaviour before customer deployment (see M5).
- **Community events** — hackathons and projectathons where you test against other vendors and learn fast.

## What's available, from whom, and where

You are not starting alone. The Caliper ecosystem exists precisely to shorten this path:

- **Caliper member services** — member organisations (including Critical Software and Vector Informatik) offer education, stacks, integration support and testing expertise.
- **Community resources** — the broader SDC/SDPi and IHE community, OR.NET heritage, and shared reference material.
- **Testing infrastructure** — Gazelle-based tooling and projectathon events (M5).

When in doubt about a specific capability, the fastest route is usually to ask a Caliper member who has done it before, rather than rediscovering it.

## Recommended first decisions for a new product team

If you do nothing else after this module, make these four decisions explicit and write them down:

1. **Scope** — which clinical use cases and which of the Big 4 functions are in v1? *This bounds everything else: every function you defer is complexity you don't pay for yet.*
2. **Connectivity option** — external module, native, or gateway? *This is the hardest decision to reverse — it shapes hardware, certification and cost.*
3. **Build vs. buy** — will you adopt an existing stack or build? (M9) *This sets your timeline and your maintenance burden for years.*
4. **MDIB-first** — who owns the MDIB design, and when does it get reviewed? *This is your public contract; an unowned MDIB is a redesign waiting to happen.*

Everything else can evolve; these four shape the cost of everything that follows.

> **◎ M4 vs. M9**
> This module is about *orientation* — finding your starting point and the first decisions. The *execution* detail (build-vs-buy, libraries, architecture patterns, a maturity roadmap) lives in **Module 9** *(coming soon)*.

---

## ✓ Learning outcomes

By the end of this module you can:

- Identify the right first steps for your specific stakeholder role.
- Understand the minimum decisions required before starting.
- Know where to find resources and who to contact in the Caliper ecosystem.

## What to do next

You have a starting roadmap. **Phase 2 (Implementation Readiness)** turns it into capability. Begin with the testing ecosystem — because knowing how your work will be verified shapes how you build it.

**→ Continue to [Module 5 · Intro to Gazelle & Caliper Testing](module-5-gazelle-caliper-testing.md)**

---

*Caliper SDPi Microlearning Series · Draft for Caliper review · v0.1 · 2026.*
