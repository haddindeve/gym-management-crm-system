# Gym Management CRM with NFC Gate Control - case study

**Engineer:** Muhammad Tanveer - Full-Stack AI Automation Engineer  
**Repository:** https://github.com/haddindeve/gym-management-crm-system

## Context

A gym needs the front desk, the membership database and the entry gate to agree with each other. Cloud-only systems fail exactly when that matters - when the internet drops and members are still queuing at the turnstile.

## What I built

A PHP/MySQL system with an offline-first browser layer: a service worker and IndexedDB keep the desk usable during an outage, and a sync engine reconciles once connectivity returns. Entry is handled by ESP32 controllers reading NFC cards and checking membership state directly, so the gate keeps working independently of the desk.

## Capabilities delivered

- Gender-aware member management
- NFC turnstile entry and exit control
- Offline-first desk operation with background sync
- Payments, expenses and staff modules
- Excel import and PDF reporting
- Licence gating for multi-site deployment

## Outcome

- Front desk stays operational through internet outages
- Gate decisions made at the hardware, not dependent on a round trip
- Members, payments and attendance in one system instead of separate books

## Source

The implementation is held in a private repository. Access can be arranged on request - [mtanveertahir66@gmail.com](mailto:mtanveertahir66@gmail.com) or [LinkedIn](https://www.linkedin.com/in/muhammad-tanveer-advenno/).