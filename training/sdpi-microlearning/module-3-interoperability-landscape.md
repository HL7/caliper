# Module 3 · SDPi in the Clinical Interoperability Landscape

> **Phase 1 — Getting Started**
> ⏱ ~10 minutes · 👥 Product, architecture and strategy stakeholders · Builds on Modules 1 & 2
> 📋 **Prerequisites:** M1 (M2a/M2b helpful) · 🧩 Self-paced · Open & free via Caliper

**Objective:** Show how SDPi fits in the full hospital interoperability picture — and, just as importantly, where it does *not* try to fit.

**You’ll learn to:** place SDPi within the broader clinical IT ecosystem, identify strategies that bridge devices to enterprise systems, and articulate the value case beyond protocol compliance.

[← M2b The Big 4 & System Functions](module-2b-big-4-and-system-functions.md) · [Series overview](README.md) · Next: [M4 But Where Do I Start? →](module-4-where-to-start.md)

---

A frequent objection from architects is "we already have HL7 and FHIR — why add another standard?" It's a fair question, and the answer is the point of this module: SDPi does a job the others were never designed to do, and the two worlds are built to work together.

## Two networks, one ecosystem

The cleanest mental model is to picture **two cooperating networks**:

- The **point-of-care network** — where SDPi/SDC lives. Devices at the bedside coordinate directly, in real time, securely, and vendor-agnostically.
- The **hospital IT network** — where HL7 V2, FHIR and DICOM live. EMR/EHR, PACS, lab, billing and analytics exchange and store healthcare information.

A **vendor-agnostic gateway** joins the two. SDPi gives you a rich, live, bi-directional picture at the bedside; the gateway translates the parts the enterprise needs into HL7/FHIR/DICOM and feeds them upstream. Together they are the foundation for an open, vendor-neutral ecosystem — which is exactly how the SDC community positions SDC and HL7/FHIR: as **complementary standards**, not rivals.

> **⌗ Key idea**
> SDPi connects **devices to each other** at the point of care. HL7 V2, FHIR and DICOM connect that world to the **enterprise**. The gateway is the bridge. No single standard does all of it.

## Integrating SDPi-enabled devices with hospital IT systems

From an architecture standpoint, SDPi devices are not meant to talk to the EMR directly. They expose a clean, standardised picture of themselves on the point-of-care network, and a gateway is responsible for the "outbound" flow of device and diagnostic data toward hospital IT, and the "inbound" flow of patient and contextual data back to bedside devices. This keeps the bedside real-time and deterministic, while the enterprise gets the consolidated, semantically-tagged data it needs — comprehensive distribution of device data to the EMR without every device needing bespoke EMR knowledge.

## Interaction with EMR/EHR, middleware and gateways

In practice the integration pattern looks like this:

**Bedside** (SDPi devices: monitors, ventilators, pumps, wearables coordinating on the point-of-care network)
→ **Bridge** (gateway / middleware: translates between SDPi/SDC and HL7 FHIR or V2; applies mapping, buffering and routing)
→ **Enterprise** (EMR/EHR & systems: stores observations, drives charting, analytics, remote monitoring and billing)

It helps to follow one value through the chain. A heart-rate reading is born on the monitor as an SDC metric in the MDIB; a subscribed gateway receives the update within moments; the gateway maps the 11073 semantics onto the enterprise representation — an HL7 V2 observation or a FHIR Observation resource — attaches the right patient identity, and forwards it; the EMR files it into the patient's chart, where it also becomes available to analytics and early-warning logic. Same clinical fact, three representations, each fit for its layer.

This is also where security boundaries are drawn deliberately. The gateway is a trust mediator: the strong, certificate-based trust model of the SDPi side has to be reconciled with whatever the connected enterprise systems expect — so the gateway's own security effectively becomes the security of the whole chain. (Module 7 goes deep on this.)

## Where SDPi sits alongside HL7 V2, FHIR, DICOM and IHE

*Module 1 introduced **what** each standard is; here the focus is **where** each sits architecturally and how they cooperate.*

| Standard | Primary job | Relationship to SDPi |
|----------|-------------|----------------------|
| **SDPi (on SDC)** | Real-time, secure device-to-device interoperability at the point of care | The bedside layer — the focus of this series |
| **HL7 V2 (incl. PCD)** | Established messaging into hospital systems | Common gateway target for device data feeds |
| **HL7 FHIR** | Modern web-API resources for apps, cloud & analytics | Gateway target; how device data reaches the wider ecosystem |
| **DICOM** | Medical imaging and related data | Coexists in the enterprise; complementary domain |
| **IHE** | Profiles that make standards interoperable and testable | SDPi *is* an IHE profile family — IHE is its home |

Notice the last row: IHE is not a competitor to SDPi at all — SDPi is published *as* an IHE profile. IHE's whole purpose is to take base standards and define how to use them so different vendors interoperate, which is precisely the role SDPi plays for devices.

## Cross-departmental workflows: OR, ICU, ER and the ward

The value case changes by setting, and architecture decisions should follow the clinical need:

- **Operating room (OR):** tight, real-time coordination between surgical and monitoring devices — the most demanding latency and safety environment, and the home of advanced "system function" scenarios.
- **Intensive care (ICU):** dense, continuous, multi-parameter monitoring per patient, where consolidation and reliable alarms matter most.
- **Emergency (ER):** rapid onboarding of whatever device is to hand — Plug-and-Trust earns its keep when there is no time to configure.
- **General ward:** the "quiet hospital" case — continuous monitoring and routing the *right* alarm to the right clinician, reducing both missed deterioration and alarm fatigue. Continuous device data is also what makes automated early-warning scores possible on the ward, instead of scores computed from observations that are hours old.

This continuity matters because patients are unmonitored far more of the time than people assume — in many wards vitals are still captured by hand every few hours, and deterioration can develop unseen between checks. Device-level interoperability is what lets monitoring be continuous instead of episodic.

## Near real-time data: alerting, analytics and remote monitoring

Because SDPi delivers a live, continuous stream rather than periodic snapshots, it unlocks a class of capabilities that batch feeds cannot:

- **Alerting** that reaches the right place quickly, including away from the bedside — the basis of the "quiet ICU/ward" and isolation-room use cases.
- **Analytics** on continuous, multi-device data — the raw material for early-warning and decision support.
- **Remote monitoring** — viewing data and, in future, controlling devices from outside the patient's room, which has demonstrated real benefits for staff safety and efficiency.

> **◎ Strategy lens**
> For product and strategy stakeholders, the clinical value case lives *above* protocol compliance. SDPi conformance is the enabler; the differentiation is the continuous-monitoring, coordination and analytics experiences it makes possible.

## Typical misunderstandings about SDPi

Three myths cause most of the confusion:

- **"SDPi replaces HL7 / FHIR."** No. They operate at different layers and are explicitly complementary; SDPi feeds into HL7/FHIR through gateways.
- **"SDPi competes with IHE."** No. SDPi *is* an IHE profile family — IHE is the framework it is published within.
- **"SDPi is just another device feed."** No. It is service-oriented, bi-directional, secure and built for device-to-device coordination — not a one-way data pipe.

Getting these straight early prevents architecture decisions that treat SDPi as a substitute for systems it was designed to *cooperate* with.

---

## ✓ Learning outcomes

By the end of this module you can:

- Recognize how SDPi fits within the broader clinical IT ecosystem.
- Identify architectural strategies that bridge SDPi-enabled devices with enterprise systems.
- Understand the clinical value case beyond protocol compliance.

## What to do next

You can now place SDPi correctly in the landscape and explain how it cooperates with enterprise standards. That completes the orientation. The next module turns orientation into action — a practical answer to the question every team asks: *"we want to do this, but where do we start?"*

**→ Continue to [Module 4 · But Where Do I Start?](module-4-where-to-start.md)**

---

*Caliper SDPi Microlearning Series · Draft for Caliper review · v0.1 · 2026.*
