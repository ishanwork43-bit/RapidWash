# RapidWash — Codex Instructions

## Purpose
RapidWash is a university Backend Engineering project and a possible future doorstep car-wash service. The immediate goal is a demonstrable MERN MVP within 15 days, with up to 5 more days for testing and extensions. Prioritize correct backend behavior, security, tests, Git history, and explainable code.

## Stack
Phase 1: HTML, CSS, vanilla JavaScript, DOM, LocalStorage.
Phase 2: React + Vite, Node.js + Express, MongoDB + Mongoose, JWT + bcrypt.
Optional (only after MVP): Socket.IO, EJS reports, Redis, Docker, FastAPI.

## Core roles and workflow
- Customer: register/login, select vehicle and wash service, view slots, create/cancel bookings, track jobs.
- Provider: view assigned jobs, update permitted booking statuses.
- Admin: manage packages, providers, bookings, and availability.
- Booking flow: select package -> server validates price and slot -> reserve safely -> provider assigned -> service completed.
- No production payments, location tracking, or real customer data in this academic MVP.

## Coding rules
- Implement only the currently requested feature; do not build the whole app at once.
- Follow docs/requirements.md and docs/architecture.md.
- Inspect relevant files before editing; do not rewrite unrelated code.
- Favor readable, modular JavaScript with routes, controllers, services, models and middleware separated.
- Validate all untrusted input on the server; enforce ownership and role authorization.
- Never trust client-supplied price or availability. Prevent double booking safely under concurrent requests.
- Include clear error responses and focused tests, including edge cases.
- Avoid unnecessary dependencies, complexity, and broad refactoring.
- Never commit secrets, .env, tokens, production identifiers or real customer data.
- Never commit or push automatically unless explicitly asked.

## After every task
Briefly report: files changed, implemented behavior, tests run/passed/failed, and two concepts the student should be able to explain in a viva. Do not claim untested features are working.
