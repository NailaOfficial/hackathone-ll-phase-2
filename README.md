# Todo Full-Stack Web App

A modern, multi-user todo application built with **spec-driven development** principles, combining a FastAPI backend with a Next.js frontend.

---

## Architecture

**Monorepo Layout:**

- `backend/` — FastAPI REST API with JWT authentication  
- `frontend/` — Next.js 16 (TypeScript, App Router)  
- `specs/` — Feature specifications & design documents  
- `.specify/` — Spec-Kit Plus configuration and templates  

---

## Tech Stack

### Backend
- **Framework:** FastAPI 0.104+  
- **ORM:** SQLModel 0.0.14+  
- **Database:** Neon Serverless PostgreSQL  
- **Authentication:** JWT (python-jose)  
- **Password Hashing:** bcrypt (passlib)  
- **Package Manager:** uv  

### Frontend
- **Framework:** Next.js 16 (App Router)  
- **Language:** TypeScript 5.x (strict mode)  
- **Authentication:** Better Auth with JWT plugin  
- **Styling:** Tailwind CSS 4  
- **UI Components:** shadcn/ui (Radix UI)  
- **Notifications:** Sonner  
- **Package Manager:** pnpm  

---

## Features

- ✅ Secure registration, login, and logout with JWT  
- ✅ Each user sees only their own tasks  
- ✅ Full CRUD for tasks (Create, Read, Update, Delete)  
- ✅ Task completion toggle (complete/incomplete)  
- ✅ Task editing and deletion with confirmation  
- ✅ Persistent data in PostgreSQL using SQLModel  
- ✅ Type-safe frontend and backend code  
- ✅ Responsive design for desktop and mobile  
- ✅ Global error handling and toast notifications  
- ✅ Skeleton loaders for better UX  
- ✅ Optimistic UI updates for instant feedback  

---

## Prerequisites

- Python 3.11+ (backend)  
- Node.js 18+ (frontend)  
- uv package manager: `pip install uv`  
- pnpm package manager: `npm install -g pnpm`  
- Neon PostgreSQL account: [https://neon.tech](https://neon.tech)  

---

## Quick Start

See detailed instructions in:  
[specs/001-todo-app-baseline/quickstart.md](specs/001-todo-app-baseline/quickstart.md)  

### Backend Setup

```bash
cd backend

# Install dependencies
uv init
uv add fastapi sqlmodel python-jose[cryptography] passlib[bcrypt] python-multipart uvicorn alembic psycopg2-binary

# Configure environment
copy .env.example .env
# Edit .env with your Neon database URL and JWT secret

# Run database migrations
alembic upgrade head

# Start server
fastapi dev src/main.py
Backend: http://localhost:8000
API docs: http://localhost:8000/docs

Frontend Setup
bash
Copy code
cd frontend

# Install dependencies
pnpm install

# Configure environment
copy .env.local.example .env.local
# Edit .env.local with API URL and Better Auth configuration

# Start development server
pnpm dev
Frontend: http://localhost:3000

Project Structure
kotlin
Copy code
phase-2/
├── backend/
│   ├── src/
│   │   ├── models/
│   │   ├── services/
│   │   ├── api/
│   │   ├── core/
│   │   └── middleware/
│   ├── tests/
│   ├── alembic/
│   └── pyproject.toml
├── frontend/
│   ├── src/
│   │   ├── app/
│   │   ├── components/
│   │   ├── lib/
│   │   └── types/
│   ├── public/
│   └── package.json
├── specs/
│   └── 001-todo-app-baseline/
│       ├── spec.md
│       ├── plan.md
│       ├── tasks.md
│       ├── data-model.md
│       ├── contracts/
│       └── quickstart.md
└── .specify/
    ├── memory/
    │   └── constitution.md
    └── templates/
Development
Run Locally
bash
Copy code
# Backend
cd backend && fastapi dev src/main.py

# Frontend
cd frontend && pnpm dev
App URL: http://localhost:3000

Database Migrations
bash
Copy code
cd backend

# Create new migration
alembic revision --autogenerate -m "description"

# Apply migrations
alembic upgrade head

# Rollback migration
alembic downgrade -1
Testing
Manual: See specs in specs/001-todo-app-baseline/spec.md
Backend: cd backend && pytest

API Documentation
Swagger UI: http://localhost:8000/docs

ReDoc: http://localhost:8000/redoc

Security
JWT tokens (expire after 24h)

Bcrypt password hashing

Multi-user isolation enforced in API and DB

HTTPS in production

No secrets in code (use env variables)

Principles
Spec-Driven Development (SDD) rules:

Spec-First: No code before approved specs

Single Code Authority: Claude Code writes implementation

Separation of Concerns: Backend/frontend boundaries

Auth Enforcement: JWT on protected endpoints

Database First: PostgreSQL + SQLModel

Observability: Structured logging & error handling

See .specify/memory/constitution.md for full rules

Documentation
Feature spec: specs/001-todo-app-baseline/spec.md

Implementation plan: specs/001-todo-app-baseline/plan.md

Task breakdown: specs/001-todo-app-baseline/tasks.md

Data model: specs/001-todo-app-baseline/data-model.md

API contracts: specs/001-todo-app-baseline/contracts/api.yaml

Setup guide: specs/001-todo-app-baseline/quickstart.md

License
[Specify your license here]

Contributing
All contributions must follow Spec-Kit Plus:

Start with a specification (/sp.specify)

Make an implementation plan (/sp.plan)

Generate tasks (/sp.tasks)

Implement only after approved tasks (/sp.implement)

See .specify/ for templates and guidance