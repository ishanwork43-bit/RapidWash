# RapidWash — Proposed Architecture

**Status: Design proposal, not implemented.**

```text
Customer / Provider / Admin
         |
  React + Vite (client/)
         | HTTPS / JSON REST
         v
 Node.js + Express (server/)
   |  routes -> controllers -> services -> Mongoose models
   |  JWT authentication + authorization
   |  validation + error handling
         |
         v
 MongoDB
   users, services, vehicles, providerSlots, bookings
```

## Collections (initial draft)
- `User`: name, email, passwordHash, role (CUSTOMER/PROVIDER/ADMIN), active.
- `Service`: title, vehicleType, durationMinutes, basePrice, active.
- `Vehicle`: ownerId, type, optional model/plate alias.
- `ProviderSlot`: providerId, date, startTime, endTime, reservedBookingId / availability state.
- `Booking`: customerId, providerId, vehicleId, serviceId, slotId, addressSnapshot, priceSnapshot, status, statusHistory, timestamps.

Final schemas will be defined and tested during implementation; avoid storing real customer data.

## Booking invariant
The server derives prices from the current Service document. A provider slot must not be allocated to more than one active booking. Use an atomic reservation operation and coherent transaction/rollback for related writes. Test simultaneous booking attempts.

## API plan
- `POST /api/auth/register`, `POST /api/auth/login`
- `GET /api/services`, admin-only `POST /api/services`
- `GET /api/slots/available`
- `POST /api/bookings`, `GET /api/bookings/my`
- `PATCH /api/bookings/:id/cancel`
- `GET /api/provider/jobs`, `PATCH /api/bookings/:id/status`
- `GET /api/admin/bookings`, `GET /api/admin/stats`

## Security and quality
- JWT verification, role checks, ownership checks and bcrypt password hashes.
- Server validation, safe error messages, secrets in ignored local .env files.
- Tests for booking conflicts, invalid status transitions, price tampering, incorrect ownership and invalid input.

## Later upgrades (not MVP requirements)
Socket.IO job status events, cache for public packages, EJS reports, Docker setup, optional FastAPI model for synthetic demand analysis.

## Main educational concepts
HTTP/request lifecycle, Node modules and event loop, Express routes/middleware, async/await, REST design, MongoDB schemas/queries, concurrency, authentication vs authorization, validation and testing.
