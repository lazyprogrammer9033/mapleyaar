# MapleYaar — Database Schema & Data Model

## Overview
This document defines the relational database model for MapleYaar. It details entities, table structures, relationships, primary keys (`PK`), foreign keys (`FK`), and constraints required to support event discovery, venue reservations, share links, and concurrency control.

---

## Entities & Table Specifications

### 1. `users` Table
Stores user account authentication and profile information.
* `id`: UUID (PK, default: `gen_random_uuid()`)
* `email`: VARCHAR(255) (UNIQUE, NOT NULL)
* `password_hash`: VARCHAR(255) (NOT NULL)
* `full_name`: VARCHAR(100) (NOT NULL)
* `phone_number`: VARCHAR(20) (NULLABLE)
* `created_at`: TIMESTAMP WITH TIME ZONE (DEFAULT: `NOW()`)

---

### 2. `venues` Table
Stores information for demo restaurants and hotels in Canada.
* `id`: UUID (PK)
* `name`: VARCHAR(150) (NOT NULL)
* `venue_type`: VARCHAR(50) (NOT NULL, Enum: `'RESTAURANT'`, `'HOTEL'`)
* `address`: VARCHAR(255) (NOT NULL)
* `city`: VARCHAR(100) (NOT NULL)
* `province`: VARCHAR(50) (NOT NULL, e.g., `'ON'`, `'BC'`, `'QC'`)
* `capacity`: INTEGER (NOT NULL, check: `capacity > 0`)
* `created_at`: TIMESTAMP WITH TIME ZONE (DEFAULT: `NOW()`)

---

### 3. `events` Table
Stores events organized by users.
* `id`: UUID (PK)
* `organizer_id`: UUID (FK -> `users.id`, NOT NULL)
* `title`: VARCHAR(150) (NOT NULL)
* `description`: TEXT (NULLABLE)
* `event_date`: TIMESTAMP WITH TIME ZONE (NOT NULL)
* `share_token`: VARCHAR(64) (UNIQUE, NOT NULL)
* `created_at`: TIMESTAMP WITH TIME ZONE (DEFAULT: `NOW()`)

---

### 4. `reservations` Table
Core inventory entity linking an event to a venue reservation.
* `id`: UUID (PK)
* `event_id`: UUID (FK -> `events.id`, UNIQUE, NOT NULL) — *One reservation per event*
* `venue_id`: UUID (FK -> `venues.id`, NOT NULL)
* `reservation_time`: TIMESTAMP WITH TIME ZONE (NOT NULL)
* `party_size`: INTEGER (NOT NULL, check: `party_size > 0`)
* `status`: VARCHAR(50) (NOT NULL, DEFAULT: `'CONFIRMED'`, Enum: `'PENDING'`, `'CONFIRMED'`, `'CANCELLED'`)
* `created_at`: TIMESTAMP WITH TIME ZONE (DEFAULT: `NOW()`)

> **Reservation Integrity Rule**: The backend/database must prevent double-booking a venue at the exact same `reservation_time` slot when `status = 'CONFIRMED'`.

---

### 5. `event_participants` Table (Junction Table)
Tracks users who join shared events.
* `id`: UUID (PK)
* `event_id`: UUID (FK -> `events.id`, NOT NULL)
* `user_id`: UUID (FK -> `users.id`, NOT NULL)
* `role`: VARCHAR(50) (NOT NULL, DEFAULT: `'GUEST'`, Enum: `'ORGANIZER'`, `'GUEST'`)
* `joined_at`: TIMESTAMP WITH TIME ZONE (DEFAULT: `NOW()`)
* **Constraint**: `UNIQUE(event_id, user_id)` — *Prevents a user from joining the same event twice.*

---

## Entity Relationships & Cardinality

| Source Entity | Relationship | Target Entity | Cardinality | FK Column |
| :--- | :--- | :--- | :--- | :--- |
| `users` | Organizes | `events` | $1 : N$ | `events.organizer_id` |
| `venues` | Holds | `reservations` | $1 : N$ | `reservations.venue_id` |
| `events` | Has | `reservations` | $1 : 1$ | `reservations.event_id` |
| `events` | Has Many | `event_participants` | $1 : N$ | `event_participants.event_id` |
| `users` | Joins | `event_participants` | $1 : N$ | `event_participants.user_id` |
