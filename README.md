# Gym Management CRM with NFC Gate Control

> Gym CRM joining member management, billing and NFC turnstile hardware, built to keep working offline.

Built by **[Muhammad Tanveer](https://www.linkedin.com/in/muhammad-tanveer-advenno/)** - Full-Stack AI Automation Engineer.

[![Source](https://img.shields.io/badge/source-private%20repository-lightgrey)](#source-code-and-access) [![Role](https://img.shields.io/badge/built%20by-Muhammad%20Tanveer-blue)](https://github.com/haddindeve)

## Contents

- [The problem](#the-problem)
- [The approach](#the-approach)
- [Architecture](#architecture)
- [Tech stack](#tech-stack)
- [Key capabilities](#key-capabilities)
- [Selected code](#selected-code)
- [Results](#results)
- [FAQ](#faq)
- [Source code and access](#source-code-and-access)
- [About the engineer](#about-the-engineer)
- [Related projects](#related-projects)

## The problem

A gym needs the front desk, the membership database and the entry gate to agree with each other. Cloud-only systems fail exactly when that matters - when the internet drops and members are still queuing at the turnstile.

## The approach

A PHP/MySQL system with an offline-first browser layer: a service worker and IndexedDB keep the desk usable during an outage, and a sync engine reconciles once connectivity returns. Entry is handled by ESP32 controllers reading NFC cards and checking membership state directly, so the gate keeps working independently of the desk.

## Architecture

| Component | Responsibility |
| --- | --- |
| **Core (PHP)** | Bootstrap, configuration, helpers and shared services |
| **Modules** | Members, attendance, payments, expenses, staff, reporting |
| **Offline layer** | Service worker, IndexedDB store and fetch interception |
| **Sync engine** | Bidirectional reconciliation after reconnect |
| **ESP32 firmware** | Entry and exit gate controllers with NFC reading |

## Tech stack

| Layer | Technology |
| --- | --- |
| Backend | PHP 8, MySQL |
| Frontend | Vanilla JavaScript PWA |
| Offline | Service worker, IndexedDB |
| Hardware | ESP32, NFC readers |
| Reporting | PDF and Excel export |

## Key capabilities

- Gender-aware member management
- NFC turnstile entry and exit control
- Offline-first desk operation with background sync
- Payments, expenses and staff modules
- Excel import and PDF reporting
- Licence gating for multi-site deployment

## Selected code

From `assets/js/offline/sync-engine.js` in the private repository:

```javascript
/*
 * Gym CRM - Sync engine
 * --------------------------------------------------------------------------
 * The brain of the offline layer. Two jobs:
 *
 *   PULL  - download every server change since the last cursor (api/sync-pull.php)
 *           into the IndexedDB "records" mirror, so data can be browsed offline.
 *   PUSH  - replay the outbox: writes the user made while offline are re-sent
 *           to the normal api/*.php endpoints, in order, once back online.
 *
 * Conflict rule (Phase 1): a replayed write that the SERVER rejects (any
 * non-OK / {success:false} response) is NOT dropped and NOT retried blindly -
 * it is moved to the "conflicts" store and surfaced to an admin to resolve.
 * Network failures (truly offline) just stay queued and retry later.
 *
 * Exposed as window.SyncEngine. No build step, no modules.
 */
(function () {
  'use strict';
```

## Results

- Front desk stays operational through internet outages
- Gate decisions made at the hardware, not dependent on a round trip
- Members, payments and attendance in one system instead of separate books

## FAQ

### Why offline-first for a gym?

Peak hours and internet outages overlap. The desk and the gate have to keep working when the connection does not.

### How does the NFC gate work?

ESP32 controllers read the member card and check membership state to open the turnstile, so entry does not wait on the web app.

### What happens to data recorded offline?

It is queued locally in IndexedDB and reconciled by the sync engine once connectivity returns.

### Is the source available?

Private repository; access on request.

## Source code and access

This repository is the public case study for **Gym Management CRM with NFC Gate Control**. The full implementation - application code, database schema, tests and deployment configuration - lives in a **private repository** on this account, alongside the rest of the work shown here.

Source access can be arranged for hiring conversations, technical review or client due diligence. The quickest route is a short message on [LinkedIn](https://www.linkedin.com/in/muhammad-tanveer-advenno/) or an email to [mtanveertahir66@gmail.com](mailto:mtanveertahir66@gmail.com).

## About the engineer

**Muhammad Tanveer - Full-Stack AI Automation Engineer**

Full-stack AI automation engineer. I build agentic systems, browser and workflow automation, RAG pipelines and the production web platforms they run on - from Rust and Python services to Next.js dashboards and PHP/MySQL business systems.

- GitHub: [haddindeve](https://github.com/haddindeve)
- LinkedIn: [Muhammad Tanveer](https://www.linkedin.com/in/muhammad-tanveer-advenno/)
- Email: [mtanveertahir66@gmail.com](mailto:mtanveertahir66@gmail.com)
- Location: Pakistan

## Related projects

- [Offline-First Restaurant POS](https://github.com/haddindeve/restaurant-pos-offline-first)
- [Lunaria - Privacy-First Women's Wellness App](https://github.com/haddindeve/lunaria-womens-wellness-app)
- [AI Sales Agent - Automated Lead Generation and Outreach](https://github.com/haddindeve/advenno-ai-sales-agent)
- [Tahir Collection - Stockinette Manufacturer Web Platform](https://github.com/haddindeve/tahir-collection-stockinette-manufacturer)
- [SMIP - Smart Manufacturing Intelligence Platform](https://github.com/haddindeve/smip-ai-iot-manufacturing-platform)
- [ARMenu - Augmented Reality Restaurant Menu SaaS](https://github.com/haddindeve/armenu-augmented-reality-menu-saas)

---

<sub>Gym Management CRM with NFC Gate Control - case study by Muhammad Tanveer - Full-Stack AI Automation Engineer. Keywords: gym management software, fitness CRM, NFC access control, ESP32 turnstile, offline-first PWA, membership management system.</sub>