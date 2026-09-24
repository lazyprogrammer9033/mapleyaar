# MapleYaar — Project Roadmap & Progress Tracker

Welcome! This document provides a high-level overview of the MapleYaar development milestones, completed checkpoints, and upcoming engineering phases.

---

## 🎯 MVP Goals
MapleYaar is a Canada-focused community & event platform allowing users to:
1. Register & authenticate securely.
2. Discover events & view venue reservations (restaurants/hotels).
3. Reserve venue slots with strict backend availability protection.
4. Share event invite links with friends.
5. Enable invitees to join events seamlessly on iOS & Android.

---

## 🚩 Project Milestones

### Phase 1: Foundations & System Design (IN PROGRESS)
* [x] **Milestone 1.1 — Version Control & Repository Setup**: Git initialization, `.gitignore`, documentation setup.
* [x] **Milestone 1.2 — Domain & Database Data Modeling**: Entities (User, Venue, Event, Reservation, Participant) and cardinality rules.
* [ ] **Milestone 1.3 — Technical Architecture Blueprint**: System design, client-server communication, directory layout.

---

### Phase 2: Backend Development (FastAPI + PostgreSQL)
* [ ] **Milestone 2.1 — Environment Setup**: Python virtual environment, FastAPI project structure, Pydantic settings.
* [ ] **Milestone 2.2 — Database Engine & Migrations**: PostgreSQL connection pooling, SQLAlchemy ORM models, Alembic migrations.
* [ ] **Milestone 2.3 — User Authentication API**: Password hashing (Bcrypt/Argon2), JWT token generation, login/signup endpoints.
* [ ] **Milestone 2.4 — Events & Venues API**: CRUD operations for demo restaurants, hotels, and user events.
* [ ] **Milestone 2.5 — Reservation Engine**: Concurrency handling, capacity checks, and table/room booking endpoints.
* [ ] **Milestone 2.6 — Event Sharing API**: Tokenized invite link generation (`/join/<token>`) and guest joining endpoints.

---

### Phase 3: Mobile Development (React Native + Expo + TypeScript)
* [ ] **Milestone 3.1 — Expo App Setup**: React Native project structure, TypeScript configuration, Navigation (React Navigation).
* [ ] **Milestone 3.2 — Auth Screens**: Login, Registration, Secure Storage for JWT tokens.
* [ ] **Milestone 3.3 — Event Discovery & Venue Screens**: Feed view, venue details, reservation booking interface.
* [ ] **Milestone 3.4 — Deep Linking & Share Integration**: Handling incoming `mapleyaar://` and web share links on iOS & Android.

---

### Phase 4: Integration, Testing & Deployment
* [ ] **Milestone 4.1 — End-to-End Testing**: Testing full flow from account creation -> reservation -> share link -> guest join.
* [ ] **Milestone 4.2 — Demo Seed Data**: Seeding 5 demo hotels, 5 demo restaurants, and fictional events.
* [ ] **Milestone 4.3 — Staging Deployment**: Hosting API backend and PostgreSQL database on cloud staging environment.

---

### Phase 5: Web / Admin Dashboard (Future Expansion)
* [ ] **Milestone 5.1 — Admin Web App**: React/Next.js interface for managing venues, viewing reservations, and managing system users.
