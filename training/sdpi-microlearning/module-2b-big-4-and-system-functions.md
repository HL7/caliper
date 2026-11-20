# Module 2b · The Big 4 Functions & System Functions

> **Phase 1 — Getting Started**
> ⏱ ~8 minutes · 👥 Mixed audience, especially newcomers to SDPi
> 📋 **Prerequisites:** M2a · 🧩 Self-paced · Open & free via Caliper

**Objective:** Explain the capabilities SDPi connectivity enables — the four core functions — and how several devices combine into clinician-meaningful system functions.

**You’ll learn to:** describe the Big 4 functions and the clinical value each delivers, explain system functions (CSF and SFC), and connect the model to a recognisable clinical scenario.

[← M2a Connectivity Fundamentals](module-2a-connectivity-fundamentals.md) · [Series overview](README.md) · Next: [M3 Interoperability Landscape →](module-3-interoperability-landscape.md)

---

> 🔎 *Technical validation pending — being reviewed by Vector Informatik.*

Module 2a covered the first three moves — find, describe, exchange. This module covers the fourth and most clinically interesting one: **coordinate**. What can SDPi-connected devices actually *do* together?

## The Big 4 functions: what they are and what each enables

SDPi's capabilities are organised into a small number of core profiles. These are the "Big 4" — the functions that, together, cover the essentials of point-of-care interoperability. Each maps to a concrete clinical value.

| Profile | Function | What it enables |
|---------|----------|-----------------|
| **SDPi-P** | Plug-and-Trust onboarding | Secure device onboarding and trust establishment — identity, certificates and authorisation built in. The foundation everything else stands on. |
| **SDPi-R** | Real-time Reporting | Live transmission of metrics and waveforms across connected devices, so a consumer always has a current, continuous picture. |
| **SDPi-A** | Alerting & Notifications | Timely, limit-based alerts shared across devices to support faster clinical response — the subject of Module 8. |
| **SDPi-xC** | External Control *(future)* | Secure external control of device functions — the basis of coordinated, closed-loop scenarios as the ecosystem matures (see Module 10). |

The four are not four independent silos — they build on each other. SDPi-P is the prerequisite: nothing else happens until a device has joined the network and established trust. Reporting and alerting ride on that trusted connection, and external control sits deliberately last, because commanding another vendor's device carries the highest clinical risk and demands the most safety and regulatory maturity. That ordering is also, roughly, the order in which most products adopt them.

A simple way to remember them: **onboard securely (P)**, **report continuously (R)**, **alert reliably (A)**, and eventually **control safely (xC)**.

> **⚑ Naming note**
> The exact naming and scope of the Big 4 is being finalised with Caliper. The four capability areas above — secure onboarding, real-time reporting, alerting, and external control — are stable; the labels may be refined in the final spec.

## System functions: CSF and SFC from a clinical workflow view

Real clinical value often comes not from one device, but from several devices cooperating to deliver a single clinical capability — a **system function**. Showing vital signs as an overlay on an endoscopic image is a system function: the oximeter contributes the data, the camera system contributes the display, and together they do something neither could alone.

Another everyday example: delivering a patient's alarm to the *right* clinician's handheld, wherever they are. The bedside device detects the condition, the alerting infrastructure routes it, and the mobile device presents it — three participants, one clinical capability. No single vendor's box "is" the function; the function emerges from their cooperation, which is exactly why it needs to be specified and coordinated deliberately.

Two roles help describe how a system function comes together, from the clinician's perspective rather than the wire's:

- **CSF — Clinician-Specified Function:** the clinical capability the care team actually wants ("show me these vitals, here, in this context"). It is framed in clinical terms, not protocol terms.
- **SFC — System Function Coordinator:** the role that orchestrates the contributing devices so the specified function is delivered safely and consistently.

At this introductory level the takeaway is simple: SDPi is built not just to move data, but to let multiple devices *combine* into clinician-meaningful functions, with clear allocation of responsibility for each contribution.

> **⚑ Naming note**
> CSF and SFC are presented here at an introductory level; their precise definitions and how much detail belongs at the intro stage are being confirmed with Caliper.

## Clinical context and coordination — and why it matters

Device data is only safe to act on if everyone agrees **which patient, which location, and which clinical situation** it belongs to. That shared understanding is **clinical context**. Coordinating context across devices — so an alarm, a waveform and a setting all refer to the same patient and episode — is what separates genuine interoperability from a pile of disconnected feeds. SDPi treats context and coordination as first-class concerns precisely because getting them wrong is a patient-safety problem, not just a data problem.

One failure mode makes the stakes vivid: a monitor is moved from bed 3 to bed 7 without its patient context being updated, and its alarms are now silently attributed to the wrong patient. Everything on the wire is technically correct — the data flows, the alarm fires — and yet the system is clinically wrong. This is why context management is profiled behaviour in SDPi, not an integration afterthought.

---

## ✓ Learning outcomes

By the end of this module you can:

- Describe the Big 4 functions and the clinical value each delivers.
- Explain what a system function is, and the roles of CSF and SFC.
- Connect the connectivity model to a recognizable clinical use scenario.

## What to do next

You now understand how devices connect (2a) and what they can do together (2b). Next we zoom out: where does all of this sit within the full hospital interoperability picture — alongside EMRs, FHIR, DICOM and IHE?

**→ Continue to [Module 3 · SDPi in the Clinical Interoperability Landscape](module-3-interoperability-landscape.md)**

---

*Caliper SDPi Microlearning Series · Draft for Caliper review · v0.1 · 2026.*
