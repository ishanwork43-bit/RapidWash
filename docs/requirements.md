# RapidWash — MVP Requirements

**Status:** Planned, not implemented. **Priority:** Chitkara University Backend Engineering evaluation first; future business capability second.

## Problem
Customers need a simple way to book doorstep car-wash services. Service providers need to see their assignments and update job status. The administrator needs one reliable view of bookings, packages, and provider availability.

## Target users and permissions
1. **Customer:** registers, logs in, saves vehicle and address details, browses packages, checks available slots, creates a booking, views own bookings, cancels when allowed.
2. **Provider:** logs in, sees only assigned jobs, updates permissible statuses.
3. **Admin:** manages services/prices, sets up providers and availability, reviews all bookings, assigns or reassigns providers, checks summaries.

Admin/provider accounts must not be created by selecting a role in an open signup form. Use a secure seeded admin and admin-only provider creation.

## Required MVP features
- Register/login, hashed passwords (bcrypt), JWT-authenticated sessions, protected routes and role/ownership checks.
- Service packages with vehicle type, duration, published price and enabled/disabled state.
- Customer vehicle and address data (fictional data for the academic demo).
- Fixed-duration provider-specific booking slots and availability lookup.
- Create booking with **server-calculated price**; reject invalid past dates, disabled services, unavailable slots and overlapping reservations.
- **Concurrency safety:** two simultaneous requests cannot reserve the same provider slot. Verify using a test.
- Booking lifecycle: PENDING -> CONFIRMED -> IN_PROGRESS -> COMPLETED; CANCELED as an allowed terminal branch. Enforce valid transitions and ownership.
- Customer booking history; provider job list; admin list/filter bookings, manage services and providers.
- Centralized error handling, input validation, consistent HTTP status codes, pagination for list APIs.
- Basic React UI for all three roles and a complete Postman/test demo.

## Important design decisions (to confirm before coding)
- MVP uses fixed slots (for example 9:00, 11:00, 14:00) rather than arbitrary overlapping time intervals.
- Keep an explicit provider-slot record and reserve with an atomic conditional update; coordinate booking writes safely, using a transaction when needed.
- Start with admin-controlled provider assignment for reliability; intelligent matching can be added later.
- No payment gateway, real OTP, GPS tracking, surge pricing, refunds or multi-city dispatch during this MVP.

## Optional after MVP
- Socket.IO live status updates; basic rate limiting; EJS printable booking receipt; Multer before/after demo images.
- Redis for an appropriate cache; Docker; one small FastAPI demonstration using synthetic booking trends.
- Kubernetes concepts in a separate lab/example if time permits; not a production requirement.

## Scope and university submission
Phase 1: small vanilla-JS prototype with DOM forms, LocalStorage and a custom slot-validation algorithm.
Phase 2: real MERN application with server-authoritative booking logic.
Maintain README, API documentation, tests, screenshots and a personal learning log. Use synthetic users/locations and do not imply official university affiliation.

## Acceptance demo
1. Customer logs in and books a published package/available slot.
2. Duplicate concurrent booking attempt is rejected without corrupting data.
3. Provider views the job and updates its status.
4. Customer sees the changed status; admin can inspect the record.
5. Unauthorized users cannot edit someone else's booking or admin-only data.
6. API validation and negative tests produce documented errors.

## 20-day target
Days 1–2: repo/Phase 1; 3–5: Node/Express/MongoDB; 6–8: authentication and safe booking; 9–11: customer UI; 12–14: provider/admin UI; Day 15: working MVP; Days 16–20: tests, documentation, deployment and selective optional features.
