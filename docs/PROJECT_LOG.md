# MapleYaar — Project Log

## Step 1 — Project Foundations & Git Setup
* **Date**: 2026-09-24
* **Status**: In Progress
* **What I did**: Initialized Git repository, configured `.gitignore`, created `docs/` directory, and established project documentation structure.
* **Why I did it**: To establish version control best practices, prevent tracking of unnecessary or sensitive files, and set up a permanent record for development progress.
* **Technology/concepts learned**: Git architecture (Working Tree, Staging Area, Repository), `.gitignore` pattern matching, and repository organization.
* **Commands used**: `git status`, `mkdir docs`, `Move-Item`, `git add`, `git commit`
* **Files created/changed**: `.gitignore`, `docs/PROJECT_LOG.md`, `docs/LEARNING_NOTES.md`
* **Important implementation details**: Placed all documentation inside `docs/` folder to keep project root clean.
* **Problems encountered**: None.
* **How the problem was solved**: N/A
* **How I verified it**: Ran `git status` to verify tracked and untracked files match expectations.
* **What I learned**: How Git separates working files from staged commits, and why early documentation setup matters for engineering projects.
* **Next step**: Complete Checkpoint 1 commit and begin architecture design for database models.



*========================================================================================*


## Step 2 — Domain & Database Data Modeling
* **Date**: 2026-09-24
* **Status**: Completed
* **What I did**: Created feature branch `feature/domain-modeling`, designed entity relationship models for Users, Venues, Events, Reservations, and Participants, and documented the database schema in `docs/DATABASE.md`.
* **Why I did it**: To establish database integrity rules (foreign keys, uniqueness, party capacity) and prevent reservation race conditions before creating SQL tables or backend APIs.
* **Technology/concepts learned**: Relational domain modeling, Primary/Foreign keys, $1:N$ and $M:N$ cardinality, Junction Tables, database constraints, Git feature branching, and merging workflows.
* **Commands used**: `git switch -c feature/domain-modeling`, `git status`, `git add`, `git commit`, `git switch main`, `git merge`
* **Files created/changed**: `docs/DATABASE.md`, `docs/PROJECT_LOG.md`, `docs/LEARNING_NOTES.md`
* **Important implementation details**: Defined `share_token` for invite URLs and enforced unique constraint on `(event_id, user_id)` in `event_participants`.
* **Problems encountered**: None.
* **How the problem was solved**: N/A
* **How I verified it**: Inspected markdown formatting and validated relational keys and cardinality rules in `docs/DATABASE.md`.
* **What I learned**: Why database schema design must precede API development, and how feature branches isolate work in Git.
* **Next step**: Finalize architecture selection for backend framework (FastAPI) and setup backend repository directory.



*========================================================================================*

## Step 3 — System Architecture & Project Roadmap Setup
* **Date**: 2026-09-24
* **Status**: Completed
* **What I did**: Created `docs/PROJECT_ROADMAP.md` to track product milestones for collaborators, and completed `docs/ARCHITECTURE.md` detailing system design, request lifecycles, and directory layout strategy.
* **Why I did it**: To establish a transparent progress tracker for team members and a clear technical blueprint for component boundaries before writing code.
* **Technology/concepts learned**: Client-Server architecture, RESTful API lifecycles, monorepo directory structuring, and technical roadmap planning.
* **Commands used**: `git status`, `git add`, `git commit`, `git push origin main`
* **Files created/changed**: `docs/PROJECT_ROADMAP.md`, `docs/ARCHITECTURE.md`, `docs/PROJECT_LOG.md`
* **Important implementation details**: Structured project repository strategy into `backend/`, `mobile/`, and `docs/`.
* **Problems encountered**: None.
* **How the problem was solved**: N/A
* **How I verified it**: Inspected markdown formatting and validated component interaction diagrams.
* **What I learned**: How architectural blueprints prevent component coupling and keep project collaborators aligned.
* **Next step**: Begin Phase 2 (Backend Setup) by creating the `backend/` directory and initializing Python virtual environment.
