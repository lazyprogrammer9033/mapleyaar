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
