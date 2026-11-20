# Module 1 · Intro to SDPi

> **Phase 1 — Getting Started**
> ⏱ ~15 minutes · 👥 Broad audience, including non-developers · Bundle: Getting Started Webinar (open)
> 📋 **Prerequisites:** none · 🧩 Self-paced · Open & free via Caliper

**Objective:** Give a practical, accessible introduction to SDPi and why it was created — in plain language, with no prior knowledge assumed.

**You’ll learn to:** explain SDPi in plain language, describe its three-volume structure and the role of profiles/options/gateways, and position SDPi relative to HL7 V2, FHIR and IHE.

[← Series overview](README.md) · Next: [M2a SDPi Connectivity Fundamentals →](module-2a-connectivity-fundamentals.md)

---

If you have ever tried to read the SDPi specification cold, you already know the problem this module solves. SDPi is powerful, but it does not explain itself in a paragraph. So let's build the picture one layer at a time.

## What SDPi is — and why it was created

**SDPi** stands for **Service-oriented Device Point-of-care Interoperability**. It is a family of *profiles* published through IHE (Integrating the Healthcare Enterprise) that says, in precise and testable terms, how medical devices at the bedside should connect, exchange data, raise alarms, and be controlled — regardless of who manufactured them.

SDPi was created to solve a problem that has dogged acute care for decades: medical devices are not built to interconnect. In many hospitals, vital signs are still transcribed by hand every four to six hours, and integrating continuous data from multiple devices remains complex, slow, and vendor-specific. The result is fragmented data, delayed clinical decisions, and patients who are effectively unmonitored most of the time. SDPi exists so that device data can flow **safely, securely, and continuously** between equipment from different vendors without a custom integration for every pairing.

It also did not appear from nowhere. The push for open, vendor-neutral device interoperability grew out of years of clinical and academic work — most visibly the OR.NET research initiative on the networked operating room — which matured into the **ISO/IEEE 11073 SDC** family of standards. SDPi is the next step in that lineage: it takes the SDC foundation and turns it into IHE profiles that vendors can implement consistently and, crucially, *test against each other*.

> **⌗ Key idea**
> SDPi is the **point-of-care interoperability profile** built on top of the **ISO/IEEE 11073 SDC** standards (Service-oriented Device Connectivity). SDC provides the technical machinery; SDPi defines the use cases, transactions and conformance rules that make it usable and testable in the real world.

## Why SDPi is harder to grasp than a typical interface spec

A normal interface specification answers a narrow question: "send these bytes to this endpoint and you'll get this response." SDPi is broader by design, and that is exactly why newcomers struggle. Three things make it different:

- **It is service-oriented, not message-oriented.** Devices don't just push messages; they expose *services* that others discover and use at runtime — more like a network of small web services than a fixed data feed.
- **It spans connectivity *and* clinical behaviour *and* safety *and* security.** A single profile family touches discovery, data modelling, alarms, remote control, trust, and regulatory evidence. You have to hold several layers in your head at once.
- **It is a layered ecosystem, not one document.** SDPi sits on SDC, which sits on web-services and networking standards, and reaches up toward HL7 for enterprise integration. Understanding any one part means knowing roughly where it sits in the stack.

This is why "just read the spec" rarely works — and why this series starts with orientation before detail.

## The concept of a profile standard

This is the single most useful mental model in this module. A **base standard** (like IEEE 11073 SDC) gives you a large toolbox of capabilities — but a toolbox alone does not guarantee that two vendors will interoperate, because each could use the tools differently.

A **profile standard** closes that gap. SDPi defines the **rules, behaviours, and conformance requirements** for interoperable medical devices: which capabilities to use, how to use them, what a compliant device must do in a given situation, and how that can be tested. In other words, the base standard says *what is possible*; the profile says *what you must do to interoperate*.

The pattern is familiar from other industries. Wi-Fi devices from hundreds of manufacturers work together not merely because IEEE 802.11 exists, but because the Wi-Fi Alliance defines certification profiles and tests products against them. SDPi plays that role for point-of-care devices: the profile plus its testing ecosystem is what turns "standards-based" into "actually interoperable."

> **◎ Analogy**
> Think of SDC as a language with a huge vocabulary. SDPi is the *style guide and grammar* that ensures two speakers actually understand each other — and a way to test that they do.

## The structure of SDPi: the three volumes

SDPi follows the familiar IHE technical-framework convention of organising its content into three volumes. Each answers a different question:

| Volume | What it contains | The question it answers |
|--------|------------------|-------------------------|
| **Volume 1** | Profiles, actors and clinical use cases — the high-level "what and why." | What does this profile enable, and who plays which role? |
| **Volume 2** | Transactions — the detailed message exchanges between actors. | Exactly how do the actors talk to each other? |
| **Volume 3** | Content and semantics — the data, nomenclature and metadata models. | What does the information mean, precisely? |

You do not need to memorise the volumes. You only need to know that when someone says "that's a Volume 2 transaction" they mean the wire-level interaction, and "Volume 3 semantics" means the meaning of the data. The three-volume split is also a practical reading guide: product and clinical stakeholders live mostly in Volume 1, developers in Volume 2, and data modellers and terminologists in Volume 3.

## Profiles, options and gateways at a high level

Three words you will hear constantly:

- **Profiles** are the named, testable capability sets. SDPi's capabilities are organised into a small number of core profiles — secure onboarding, real-time reporting, alerting, and (in future) external control. Module 2b covers these "Big 4" in detail.
- **Options** are well-defined add-ons within a profile. They let a device declare extra, optional behaviour without breaking the baseline that everyone must support.
- **Gateways** are the bridges between the point-of-care SDPi world and the enterprise world. A gateway translates between SDPi/SDC at the bedside and standards like HL7 FHIR or V2 used by EMRs, middleware and analytics. Gateways are how device data reaches the rest of the hospital — for example, a ventilator's live settings and measurements arriving in the EMR flowsheet without anyone typing them in.

> **⌗ Remember**
> Profiles = capabilities. Options = optional extensions. Gateways = bridges to the enterprise. Everything else in SDPi hangs off these three ideas.

## SDPi vs. HL7 PCD V2 vs. FHIR — what each is, and where it fits

These three are **complementary, not competing**. A common misconception is that SDPi "replaces" HL7. It does not. They operate at different points in the journey of a piece of device data.

| | **SDPi (on SDC)** | **HL7 PCD V2** | **HL7 FHIR** |
|---|---|---|---|
| What it is | Point-of-care, device-to-device interoperability profile | Classic HL7 V2 messaging for Patient Care Devices | Modern web-API standard for health data resources |
| Where it lives | The clinical / point-of-care network, at the bedside | Between devices/gateways and hospital systems | The enterprise & ecosystem (EMR, apps, analytics) |
| Strength | Real-time, bi-directional, secure, vendor-neutral device coordination | Ubiquitous, well-understood device-to-system feeds | Flexible REST resources, easy app and cloud integration |
| Typical use | A monitor and a ventilator coordinating safely in the OR | Sending periodic vitals into an EMR as a message | Querying an Observation from a clinical app |

The clean way to hold it: **SDPi connects devices to each other** in real time at the point of care; **HL7 V2 and FHIR connect that world to the enterprise** — usually through a gateway.

*That is the conceptual placing — all we need here. **Module 3** goes further: how SDPi sits architecturally alongside these standards in a live hospital (gateways, EMR/EHR, cross-department workflows).*

## The role of SDPi in Plug-and-Trust device interoperability

**Plug-and-Trust** is the vision SDPi is built to deliver: a device from any compliant vendor can join the clinical network and be *trusted automatically* — its identity verified, its role authorised, its data encrypted — without bespoke integration work. "Plug-and-play" gets devices talking; "Plug-and-Trust" adds the security and identity layer that healthcare demands.

A worked example from the SDC community makes it concrete: showing a patient's vital signs as an overlay inside an endoscopic image. The pulse oximeter *provides* the vital signs; the endoscopic camera system *displays* them; the hospital provides the trusted medical IT network that lets the two cooperate safely. Each plays a defined role, and trust is established by design rather than by manual configuration.

> **◎ In one line**
> Plug-and-play asks "can these devices talk?" Plug-and-Trust asks "can they talk *and* should they trust each other?" SDPi is designed to answer yes to both.

## Why vendors, providers and ecosystem partners should care now

The timing matters. Adoption is accelerating: major manufacturers such as Philips, GE HealthCare and Dräger are actively promoting the ISO/IEEE 11073 family to replace proprietary protocols, and SDPi is the profile bringing this to a testable, regulatory-friendly footing — including its arrival in the US ecosystem through the HL7 Devices Accelerator. Analysts put the medical-device-interoperability market on a path of more than 20% annual growth toward multi-billion-dollar scale by 2030.

There is also a simple economic argument underneath. Proprietary integration scales badly: every new vendor pairing is another custom interface to build, test, and maintain — an N×M problem. A shared profile turns that into N+M: each vendor implements and tests against the profile once, and interoperability with every other conformant participant follows. That is where the integration cost savings actually come from.

- **Vendors** can integrate faster with a standards-based approach — no custom interface for every customer pairing — and avoid being seen as lagging as buyers begin to expect SDC compliance.
- **Providers (hospitals)** gain continuous, real-time visibility across care settings and reduced integration cost and lock-in.
- **Ecosystem partners** — middleware, analytics, app developers — get a vendor-neutral, open foundation to build on.

The cost of waiting is real: getting the connectivity model wrong, or betting on proprietary integration, becomes expensive rework later.

---

## ✓ Learning outcomes

By the end of this module you can:

- Explain the purpose of SDPi in plain language.
- Describe the three-volume structure and the role of profiles, options, and gateways.
- Correctly position SDPi relative to HL7 V2, FHIR, and IHE.

## What to do next

You now have the vocabulary. The natural next step is to see how SDPi connectivity actually works — how devices discover each other, what data they expose, and the four core capabilities that make it useful in a clinical setting.

**→ Continue to [Module 2a · SDPi Connectivity Fundamentals](module-2a-connectivity-fundamentals.md)**


---

*Caliper SDPi Microlearning Series · Draft for Caliper review · v0.1 · 2026.*
