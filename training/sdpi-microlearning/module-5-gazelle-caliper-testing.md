# Module 5 · Intro to Gazelle and Caliper Testing

> **Phase 2 — Implementation Readiness**
> ⏱ ~10 minutes · 👥 Developers, testers, technical leads and product managers
> 📋 **Prerequisites:** M4 · 🧩 Self-paced · Open & free via Caliper

**Objective:** Show how the Caliper testing ecosystem supports SDPi adoption from development through deployment.

**You’ll learn to:** recognise the SDPi/Caliper testing stages, connect tooling to deployment readiness, and treat testing events as an enablement asset.

[← M4 But Where Do I Start?](module-4-where-to-start.md) · [Series overview](README.md) · Next: [M6 Regulatory Overview →](module-6-regulatory-overview.md)

---

> 🔎 *Technical validation pending — being reviewed by Vector Informatik.*

A profile is only as good as your ability to prove you conform to it. This module introduces the tooling and events that make SDPi conformance and interoperability **verifiable** — and explains why you should engage with them early, not at the end.

## Why structured test tooling matters before deployment

Interoperability bugs are cheap to find in a test harness and very expensive to find at a customer site. Field experience is blunt about where the pain concentrates: discovery misconfiguration, real-time latency, and mismatched MDIB handles cause most lost time — and all are catchable with the right tooling, run early. Structured testing converts "we think it interoperates" into "we have demonstrated it interoperates, repeatably."

That word *repeatably* is doing real work. SDPi testing is built around published **test definitions**: each one states the preconditions, the steps, and the observable behaviour a conformant implementation must show. Because the definitions are shared, two vendors who have never met can test against the same yardstick — and a regulator or customer can understand exactly what "passed" means.

> **⌗ Key idea**
> Testing in SDPi is not a final gate — it's a development accelerator. The teams that test discovery and measure latency on day one ship faster than those that defer testing to integration.

## What Gazelle is

**Gazelle** is the open testing platform long used by the **IHE** community to support interoperability testing — managing test definitions, partner registration, conformance checks and the logistics of testing events. Because SDPi is an IHE profile family, Gazelle is the natural foundation for SDPi conformance and interoperability testing: it gives vendors a common, neutral place to validate that their implementation behaves as the profile requires.

## Gemini today, and the evolution toward Caliper tooling

The tooling is evolving. **Gemini** represents the current generation of SDC/SDPi test support, and the trajectory is toward **Caliper-hosted tooling** purpose-built for the SDPi ecosystem. For a product team the practical message is simple: build against the standard and the published test definitions, and expect the supporting tools to keep improving under the Caliper umbrella.

## The testing progression

SDPi testing follows a staged progression, from solo self-testing toward multi-vendor, community validation. Each stage increases confidence and realism:

| Stage | What happens | Confidence gained |
|-------|--------------|-------------------|
| **PAT** | Pre-event / self-assessment testing against the test definitions, on your own. | "My implementation passes the defined tests." |
| **CAT** | Tool-assisted / connectathon-style testing, often with a partner or reference system. | "I interoperate with at least one other system." |
| **CA** | Conformity assessment — a more formal evaluation of conformance. | "My conformance has been independently assessed." |
| **Projectathons** | Supervised multi-vendor interoperability events. | "I interoperate with many vendors, under realistic conditions." |

> **⚑ Naming note**
> The exact definitions and scope of the PAT / CAT / CA stages are being finalised with Caliper. The *progression* — self-test → assisted/peer test → conformity assessment → community projectathon — is the stable concept to carry forward; the labels may be refined.

## Why community testing events improve quality

A projectathon does something no lab can: it puts your device in a room with many other vendors' implementations and surfaces the disagreements that only appear under real diversity — subtly different MDIB modelling, edge-case discovery behaviour, alerting mismatches. These events are an **enablement asset**, not just a compliance checkbox: teams routinely leave with a sharper implementation and relationships with other implementers.

## A field perspective: what to actually test

Grounded in hands-on SDC work, these are the test areas that repay early attention:

- **Discovery first** — verify WS-Discovery (multicast route, network adapter, firewall) before building features; silent discovery failures waste the most time.
- **Latency early** — benchmark real-time data as soon as a provider + consumer exist; waveform performance depends on getting batch sizing right.
- **Connection robustness** — single- and multi-device stability, range boundaries, reconnection behaviour.
- **Metadata & semantics** — units, accuracy, acquisition intervals, and that MDIB metadata matches the real device.
- **Waveform integrity** — sample ordering, sampling rate, no duplicates, visible timestamp gaps.

And make it continuous, not ceremonial: fold the conformance tests into your regular regression suite, and re-run them after every MDIB change. An interoperability test that runs once before an event catches one class of bug; the same test running in CI catches regressions for the life of the product.

## How to engage with Caliper testing resources

The practical path: build against the current test definitions, use the available Gazelle/Gemini tooling to self-test (PAT), find a partner system to test against (CAT), and register for the next projectathon to validate broadly. Caliper member organisations can help you prepare for and get the most out of these events.

---

## ✓ Learning outcomes

By the end of this module you can:

- Recognize the major testing stages in the SDPi and Caliper ecosystem.
- Understand how tooling connects product development to deployment readiness.
- See testing events as an enablement asset, not just a compliance step.

## What to do next

You've seen how implementation work is verified. The remaining modules cover **Phase 3 — Deployment Readiness**: the assurance topics that must be addressed before anything goes near a patient. (If you're following the Implementation Readiness bundle, M9 Implementation Pathways is coming soon.)

**→ Continue to [Module 6 · Regulatory Overview](module-6-regulatory-overview.md)**

---

*Caliper SDPi Microlearning Series · Draft for Caliper review · v0.1 · 2026.*
