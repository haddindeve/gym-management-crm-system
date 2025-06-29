# Gym Management CRM with NFC Gate Control - architecture

A PHP/MySQL system with an offline-first browser layer: a service worker and IndexedDB keep the desk usable during an outage, and a sync engine reconciles once connectivity returns. Entry is handled by ESP32 controllers reading NFC cards and checking membership state directly, so the gate keeps working independently of the desk.

## Components

### Core (PHP)

Bootstrap, configuration, helpers and shared services

### Modules

Members, attendance, payments, expenses, staff, reporting

### Offline layer

Service worker, IndexedDB store and fetch interception

### Sync engine

Bidirectional reconciliation after reconnect

### ESP32 firmware

Entry and exit gate controllers with NFC reading

## Stack

| Layer | Technology |
| --- | --- |
| Backend | PHP 8, MySQL |
| Frontend | Vanilla JavaScript PWA |
| Offline | Service worker, IndexedDB |
| Hardware | ESP32, NFC readers |
| Reporting | PDF and Excel export |

Designed and implemented by Muhammad Tanveer - Full-Stack AI Automation Engineer.