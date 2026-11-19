# RapidWash

**On-Demand Doorstep Car Wash Booking & Service Management Platform**

RapidWash is a university-first MERN project designed to demonstrate secure REST APIs, scheduling, role-based access, database consistency, testing, and a full booking workflow. It is also intended as a foundation for a possible future car-wash business.

> **Status: Project planning and repository setup. The application is not implemented yet.**

## Problem and solution

Customers need a simple way to book doorstep car washing. Service providers need a list of assigned jobs. Administrators need to manage packages, booking availability, and operations. RapidWash connects these three roles through one booking platform.

## Planned MVP

- Customer signup/login, service selection, vehicles and booking history.
- Provider job list and status updates.
- Admin management of services, providers and bookings.
- Provider-specific slot availability and **double-booking prevention**.
- Server-calculated prices, JWT authentication, bcrypt, authorization and validation.
- React UI, Express REST API and MongoDB/Mongoose persistence.
- Tests, API docs, example requests and a complete demonstration.

Real payments, OTP verification, live GPS and automated refunds are **out of scope** for the university MVP.

## Technology

| Layer | Planned stack |
| --- | --- |
| Phase 1 prototype | HTML, CSS, vanilla JavaScript, DOM, LocalStorage |
| Client | React, Vite, Tailwind CSS |
| Backend | Node.js, Express.js |
| Database | MongoDB, Mongoose |
| Security | JWT, bcrypt, validation, role-based access |
| Testing | API tests and Postman |
| Extensions, only if time permits | Socket.IO, EJS, Redis, Docker, FastAPI |

## Planned repository layout

```text
rapidwash/
  phase-1/       # Browser prototype, built first
  client/        # React app
  server/        # Express API
  docs/          # Requirements, architecture, API docs, learning log
  examples/      # Focused syllabus exercises
  ai-service/    # Optional later
  AGENTS.md      # Instructions for Codex
  README.md
  .gitignore
  .env.example
```

Git does not track empty directories; folders will appear as actual work is added.

## Project documents

- [MVP requirements and acceptance criteria](docs/requirements.md)
- [Proposed backend architecture and API plan](docs/architecture.md)
- [Personal learning and viva log](docs/learning-log.md)
- [Codex development instructions](AGENTS.md)

## Roadmap

1. **Days 1–2:** Phase 1 browser prototype and GitHub foundation.
2. **Days 3–5:** Node.js, Express, MongoDB and models.
3. **Days 6–8:** JWT authentication, secure booking workflow and concurrency tests.
4. **Days 9–11:** Customer-facing React booking flow.
5. **Days 12–14:** Provider/admin dashboards, integration and tests.
6. **Day 15:** Working, demonstrable MVP.
7. **Days 16–20:** Documentation, deployment, security checks, optional advanced syllabus demonstrations and viva.

## Local setup

Setup commands will be documented once the client and server applications are implemented. Do not expect this planning-stage repository to run as an application yet.

**Security:** Never commit real passwords, JWT secrets, API tokens, or real customer information. Copy sample environment variables from `.env.example` into an ignored local `.env` file when the backend is created.

## Academic demonstration

The project is independently developed for backend engineering learning and evaluation. It is **not** an official university service and uses synthetic customer/provider data. Development progress and test evidence will be recorded in GitHub commits and `docs/learning-log.md`.
