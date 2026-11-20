# Module 2a · SDPi Connectivity Fundamentals

> **Phase 1 — Getting Started**
> ⏱ ~10 minutes · 👥 Mixed audience, especially newcomers and developers
> 📋 **Prerequisites:** M1 · 🧩 Self-paced · Open & free via Caliper

**Objective:** Explain how SDPi-based connectivity actually works — discovery, the data model, and device-to-device interoperability — for newcomers, with the clinical "so what" for each idea.

**You’ll learn to:** explain how SDPi devices discover and exchange data, describe the MDIB and why it is the device's contract, and explain device-to-device Plug-and-Trust interoperability.

[← M1 Intro to SDPi](module-1-intro-to-sdpi.md) · [Series overview](README.md) · Next: [M2b The Big 4 & System Functions →](module-2b-big-4-and-system-functions.md)

---

> 🔎 *Technical validation pending — being reviewed by Vector Informatik.*

Module 1 gave you the vocabulary. Now we open the hood — not to make you an engineer, but so the rest of the series makes sense. SDPi connectivity reduces to three moves: **find** each other, **describe** what you are, and **exchange** data securely. (The fourth move — *coordinate* — is Module 2b.)

## How SDPi devices discover each other and exchange data

On an SDPi clinical network there is no central server that has to be configured to know about every device. Instead, devices announce themselves and find each other automatically. This is what makes "plug-and-play" possible.

1. **Discover** — A device joins the network and uses **WS-Discovery** to announce itself and find others, via lightweight multicast "Hello / Probe" messages.
2. **Describe** — It exposes its capabilities as **services** over DPWS / SOAP, so a consumer can ask "what can you do, and what data do you have?"
3. **Secure** — Communication runs over **TLS with mutual X.509 authentication** — each side proves its identity before any data flows.
4. **Exchange** — Consumers **subscribe** to live data and receive updates — numerics, waveforms, alarms — as they change.

To make it concrete, picture a patient monitor being wheeled into a room and powered up. It announces itself on the network with a "Hello"; a consumer — say, a central station or a gateway — probes it, reads its description, and both sides authenticate each other's certificates. Seconds later the consumer has subscribed, and heart rate, SpO₂ and alarm states are streaming — with no one having configured an interface. That whole sequence *is* the four steps above.

The key shift from older device feeds is the **service-oriented** model: a device is not a fixed cable carrying one data stream, it is a provider of services that any authorised consumer can discover and use at runtime. Two roles recur throughout SDPi: a **provider** (a device that exposes data and operations) and a **consumer** (something that discovers and uses them).

## The data model: what a device exposes, and how it's structured

For two devices to truly understand each other, they need a shared way to describe information. In SDPi/SDC that description is the **MDIB — the Medical Device Information Base**. The MDIB is the heart of the system: every measurement, alarm and operation a device offers is modelled there as a structured, hierarchical description.

The MDIB separates two things cleanly:

- **Descriptors** — the *static* definition: what exists. "This device has a heart-rate metric, measured in bpm, with these alarm limits."
- **States** — the *dynamic* values: what is true right now. "Heart rate is currently 72 bpm; this alarm is currently present."

If you come from software, the split will feel familiar: descriptors are like the *class definition* or blueprint, states are like the *live instance values*. Consumers can rely on the blueprint staying stable while the readings change beneath it.

Information is organised as a nested tree, which is easier than it looks:

| Level | Meaning |
|-------|---------|
| **MDS** — Medical Device System | The device as a whole (e.g. a patient monitor). |
| **VMD** — Virtual Medical Device | A functional sub-unit within it. |
| **Channel** | A grouping of related measurements. |
| **Metric** | An individual value — a numeric (heart rate), a waveform, or a text value. |
| **Alert System** | The alarm sub-system: conditions and the signals that announce them. |
| **SCO** — Service Control Object | The operations a consumer can invoke on the device. |

Read top-down with an example: a patient monitor (MDS) contains an SpO₂ module (VMD), which groups its measurements in a channel, which contains the SpO₂ percentage as a numeric metric and the plethysmogram as a waveform metric. Every value a consumer ever receives has an address somewhere in this tree.

> **⌗ Key idea**
> The MDIB is the device's **contract**. If you remember one engineering principle from this module, it's that good SDPi work starts by designing the MDIB — it is the API every other device relies on.

## Device-to-device Plug-and-Trust interoperability — the big picture

Put discovery and the data model together and you get **device-to-device (D2D) interoperability at the point of care**: monitors, ventilators, pumps and sensors cooperating directly and securely on the clinical network, each trusting the others' identity and role. This is the bedside foundation that Module 1's "Plug-and-Trust" vision describes — devices that not only connect, but are authenticated and authorised by design.

It has been proven to work in practice, not just on paper: independent implementations — for example a Python-based consumer and a C++-based embedded provider — can discover one another and exchange data because they share the same MDIB schema, discovery mechanism and service contracts. That cross-implementation interoperability is the whole point.

## Why getting the connectivity model right from the start avoids expensive rework

Connectivity decisions are foundational: the MDIB design, the discovery configuration and the performance characteristics of real-time data all ripple through everything built on top. Field experience is blunt about this — the most painful problems (waveform latency, silent discovery failures, mismatched handles) trace back to early modelling and configuration choices, and they cost an order of magnitude more to fix after the fact than to get right on day one.

The asymmetry is worth spelling out: an MDIB structure is cheap to change on a whiteboard, awkward to change once a consumer depends on it, and very expensive to change once devices are fielded — because every consumer that learned your contract has to relearn it.

> **◎ Practical guidance**
> Teams that succeed tend to do three things early: **design the MDIB first** (it's your contract), **verify discovery before building features**, and **measure real-time performance as soon as a provider and consumer exist** — not at integration time.

---

## ✓ Learning outcomes

By the end of this module you can:

- Explain how SDPi connectivity works in plain language (discover, describe, secure, exchange).
- Describe the MDIB — descriptors vs. states, and the MDS→Metric hierarchy — and why it is the device's contract.
- Explain device-to-device Plug-and-Trust interoperability at the point of care.

## What to do next

You understand how devices connect and describe themselves. Next: what they can actually *do* together — the four core functions and how multiple devices combine into clinician-meaningful system functions.

**→ Continue to [Module 2b · The Big 4 Functions & System Functions](module-2b-big-4-and-system-functions.md)**

---

*Caliper SDPi Microlearning Series · Draft for Caliper review · v0.1 · 2026.*
