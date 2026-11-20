# Module 6 · Regulatory Overview

> **Phase 3 — Deployment Readiness**
> ⏱ ~10 minutes · 👥 Regulatory, quality, product and architecture stakeholders
> 📋 **Prerequisites:** none (M1 helpful) · 🧩 Self-paced · Open & free via Caliper

**Objective:** Frame the regulatory conversation for SDPi clearly and without overpromising.

**You’ll learn to:** explain why conformance is not clearance, how interoperability evidence feeds a submission, and why you need a product-specific regulatory strategy.

[← M5 Gazelle & Caliper Testing](module-5-gazelle-caliper-testing.md) · [Series overview](README.md) · Next: M7 Cybersecurity & Plug-and-Trust *(coming soon)*

---

> **ℹ️ Not legal or regulatory advice**
> This module builds shared understanding so engineering, product and regulatory teams can talk to each other. It is **not** regulatory advice. Treatment varies by device class, claims, and jurisdiction — confirm specifics with your regulatory function and the relevant authority.

SDPi work generates strong interoperability evidence. The risk is in how that evidence is *described*. This module helps you make accurate claims and avoid the overpromising that creates audit and credibility problems later.

## The principle that frames everything: conformance is not clearance

The single most important regulatory message about SDPi:

> **⌗ Key principle**
> **Standards conformance alone does not equal regulatory clearance.** Conforming to SDPi proves your device behaves as the profile requires. It does *not*, by itself, make a device approved, cleared, or safe for a specific clinical use. Conformance is an input to a regulatory submission, not a substitute for one.

## Why interoperability claims need evidence and clear boundaries

An interoperability claim is a claim about *system behaviour*, and regulators expect it to be bounded and evidenced. "Our device is interoperable" is meaningless without answering: interoperable with what, under which profile and options, doing which functions, within which system boundary? Defining that boundary precisely — what is inside your device's responsibility and what is not — is the foundation of a defensible claim.

The difference is easiest to see side by side. A vague claim says: *"The device is SDC/SDPi interoperable."* A well-bounded claim says something like: *"The device implements the SDPi [profile/option set], acting as a provider of [these functions], verified against [these test definitions]; system-level behaviour when combined with other devices is outside the device's own claims."* The second version is longer — and defensible, auditable, and honest about its limits.

## What "test to interface" means — and what it does not cover

**Testing to the interface** means verifying that your device correctly implements the SDPi interface: the right transactions, the right MDIB content, conformant behaviour at the boundary. That is valuable and necessary.

What it does **not** cover: the clinical safety and effectiveness of the *overall system function* delivered by multiple devices, the behaviour of the other participants, or the risks that emerge only when devices are combined in a specific clinical workflow. Interface conformance is necessary but not sufficient for a clinical claim.

## What "regulatory submission ready" should — and shouldn't — imply

| It **should** imply | It should **not** imply |
|---------------------|-------------------------|
| You have structured conformance and interoperability evidence | That the device is cleared or approved |
| Clear system boundaries and defined claims | That clinical safety/effectiveness is proven by conformance alone |
| Evidence that contributes to a submission package | That no risk analysis specific to your product is needed |
| Traceability between standards used and claims made | That the same package works for every market unchanged |

Using "submission ready" loosely is a common trap — be precise about what your SDPi evidence does and does not establish.

## The open question: will the FDA ever approve a Plug-and-Trust device?

This is a genuinely open question in the community, and it's worth understanding what it really asks. Plug-and-Trust envisions devices that join and cooperate *automatically*, with trust established by design. Regulators, however, evaluate defined devices making defined claims with defined risk controls. The hard part isn't the technology — it's framing accountability and risk control for a system whose exact composition isn't known in advance. The realistic near-term path is product-by-product clearance of devices that *support* SDPi functions, with the system-level "plug-and-trust" assurance evolving alongside regulatory thinking — rather than a single blanket approval of "a Plug-and-Trust device."

## Conformance, risk controls and product claims — how they relate

Think of three connected layers:

- **Standards conformance** — you implement SDPi correctly (verified via M5 testing).
- **Risk controls** — you identify and mitigate the hazards your product introduces or relies on, including those at the interoperability boundary (alerting is a prime example — see M8).
- **Product claims** — what you tell the market and the regulator, bounded by the two layers above.

Claims must be *supported by* risk controls and conformance evidence — never run ahead of them.

## Frameworks you'll encounter

These are the standards and regulations commonly relevant to connected, interoperable medical devices. Map your work to the ones that apply to your device and market:

| Framework | Concerns |
|-----------|----------|
| **EU MDR** | Medical Device Regulation — data integrity, cybersecurity, clinical safety |
| **EU CRA** | Cyber Resilience Act — security obligations for connected products |
| **IEC 62443-4-1** | Secure product development lifecycle |
| **IEC 81001-5-1** | Health software security in the product lifecycle |
| **IEC TR 60601-4-5** | Safety-related technical security for medical devices |
| **ISO/IEC 80001** | Risk management for IT networks incorporating medical devices |
| **ISO 27001** | Information security management |
| **FDA cybersecurity guidance** | Pre-/post-market cybersecurity, patching and vulnerability disclosure |

## Positioning SDPi within a regulatory evidence strategy

SDPi conformance and interoperability testing are powerful *inputs* to your evidence package: they demonstrate disciplined, standards-based interface behaviour. Position them as part of a **risk-based, product-specific** strategy — combined with your own hazard analysis, clinical evaluation and security case — rather than as the whole story.

Two practical habits make this dramatically easier. First, involve the regulatory function *early* — when use cases and claims are being chosen, not when the evidence package is being assembled — so the claims strategy shapes the engineering work instead of chasing it. Second, capture evidence as you go: test reports, MDIB design rationale, traceability from profile requirements to verification results. Evidence reconstructed at submission time is always weaker, and more expensive, than evidence collected while the work was happening.

---

## ✓ Learning outcomes

By the end of this module you can:

- Understand that standards conformance alone does not equal regulatory clearance.
- Explain how interoperability evidence contributes to a submission package.
- Identify the need for a risk-based, product-specific regulatory strategy.

## What to do next

Regulatory claims rest on risk controls — and in connected devices, security is one of the biggest. Next, the trust foundations that make Plug-and-Trust trustworthy.

**→ Module 7 · Cybersecurity & Plug-and-Trust is coming soon.** Meanwhile, see the [series overview](README.md) for the full learning path.

---

*Caliper SDPi Microlearning Series · Draft for Caliper review · v0.1 · 2026.*
