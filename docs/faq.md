# Gym Management CRM with NFC Gate Control - frequently asked questions

## Why offline-first for a gym?

Peak hours and internet outages overlap. The desk and the gate have to keep working when the connection does not.

## How does the NFC gate work?

ESP32 controllers read the member card and check membership state to open the turnstile, so entry does not wait on the web app.

## What happens to data recorded offline?

It is queued locally in IndexedDB and reconciled by the sync engine once connectivity returns.

## Is the source available?

Private repository; access on request.

## Can I see the source code?

The implementation is in a private repository. Access can be arranged for hiring or technical review - [mtanveertahir66@gmail.com](mailto:mtanveertahir66@gmail.com).

## Who built Gym Management CRM with NFC Gate Control?

Muhammad Tanveer - Full-Stack AI Automation Engineer. Full-stack AI automation engineer. I build agentic systems, browser and workflow automation, RAG pipelines and the production web platforms they run on - from Rust and Python services to Next.js dashboards and PHP/MySQL business systems.