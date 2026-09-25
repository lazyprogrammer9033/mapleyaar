# MapleYaar — Technical Architecture Blueprint

## System Architecture Overview

```text
[ Mobile App (iOS / Android) ]            [ Web / Admin Panel ]
 (React Native + Expo + TS)               (Next.js / React)
             \                                    /
              \                                  /
               v                                v
       +------------------------------------------------+
       |               FastAPI Backend                  |
       |  - Auth Middleware (JWT)                       |
       |  - Pydantic Validation                         |
       |  - Routers: Auth, Venues, Events, Reservations |
       +-----------------------+------------------------+
                               |
                               v
       +------------------------------------------------+
       |              PostgreSQL Database               |
       |  - Relational tables & Foreign Key constraints |
       |  - Row-level transactions for reservations     |
       +------------------------------------------------+


MapleYaar/
├── docs/                 # Documentation & architectural records
│   ├── PROJECT_LOG.md
│   ├── LEARNING_NOTES.md
│   ├── DATABASE.md
│   ├── PROJECT_ROADMAP.md
│   └── ARCHITECTURE.md
├── backend/              # Python FastAPI server & database models (Phase 2)
└── mobile/               # React Native Expo mobile app (Phase 3)



---

### Step 2: Update [`docs/PROJECT_ROADMAP.md`](file:///c:/Users/patel/OneDrive/Documents/CODE%20EDITORS/ANTIGRAVITY%20CODE%20EDITOR/MapleYaar/docs/PROJECT_ROADMAP.md)
In [`docs/PROJECT_ROADMAP.md`](file:///c:/Users/patel/OneDrive/Documents/CODE%20EDITORS/ANTIGRAVITY%20CODE%20EDITOR/MapleYaar/docs/PROJECT_ROADMAP.md):
1. Update line 19 to:
   ```markdown
   ### Phase 1: Foundations & System Design (COMPLETED)
