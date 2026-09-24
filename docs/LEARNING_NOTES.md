# MapleYaar — Learning Notes

## 1. Version Control & Git

### What it is
Git is a distributed version control system that tracks changes in source code over time.

### Why MapleYaar uses it
To safely maintain a complete history of our codebase, experiment with new features in branches without breaking production code, and collaborate effectively.

### What problem it solves
Eliminates manual file duplication (e.g. `main_v2_final.py`), prevents code loss, and allows rolling back to previous working versions if bugs are introduced.

### How it works
Git takes snapshots of the project state. It manages changes through three stages:
1. **Working Directory**: The actual files you are editing.
2. **Staging Area**: The draft area where you select changes to commit.
3. **Repository**: The database where committed snapshots are permanently stored.

### Important Terminology
* **Repository (Repo)**: The folder containing your project files and the `.git` metadata directory.
* **Commit**: A recorded snapshot of staged changes with an author name, timestamp, and message.
* **Hash (SHA)**: A unique identifier (e.g., `a1b2c3d...`) generated for every commit.
* **Branch**: An independent line of development.
* **`.gitignore`**: A configuration file defining patterns of files Git should not track.

### Common Mistakes
* Committing secret keys or `.env` files to Git.
* Writing vague commit messages like `"fix bugs"` or `"updated stuff"`.
* Forgetting to check `git status` before committing.

*========================================================================================*

## 2. Relational Database & Data Modeling

### What it is
Data modeling is the process of defining how real-world data (users, events, hotel rooms) is structured, stored, and connected in a database.

### Why MapleYaar uses it
To ensure event reservations are strictly tracked and protected against double bookings or orphan records.

### Important Terminology
* **Primary Key (PK)**: A unique identifier (UUID/integer) for each row in a database table.
* **Foreign Key (FK)**: A column referencing a Primary Key in another table to establish relationships.
* **Junction Table (Join Table)**: A table used to break down a Many-to-Many ($M : N$) relationship into two One-to-Many ($1 : N$) relationships.
* **UUID (Universally Unique Identifier)**: A 128-bit value (e.g. `123e4567-e89b-12d3-a456-426614174000`) used as a globally unique primary key instead of sequential integers (which can reveal business metrics or be vulnerable to enumeration attacks).
* **Race Condition**: A flaw where two system processes try to reserve the same inventory simultaneously, potentially causing double bookings if database-level locking is missing.
