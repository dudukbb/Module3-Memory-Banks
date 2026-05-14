# Architecture Overview - Personal Task Board (mrello)

## Project Summary

Taskboard/mrello is a lightweight real-time task management web application for small engineering teams.

Core capabilities:
- secure authentication and onboarding
- Kanban-style task board with assignment and due dates
- real-time collaboration and online presence
- email notifications and reminders

## 1. System Architecture

### Pattern
Microservices with a web frontend:
- Next.js 14 frontend (`apps/web`)
- Express.js services behind a gateway
- PostgreSQL 16 + Prisma 5 for data access

### Core Services
- `auth-service`: registration, login, JWT issuance, session persistence, password reset
- `board-service`: task CRUD, Kanban board operations, assignment, due dates
- `notification-service`: email notifications and due date reminders
- `gateway-service`: API gateway routing, rate limiting, shared edge middleware

## 2. Frontend Architecture

- Framework: Next.js 14+ App Router
- UI: React + Tailwind CSS 3.x
- State management: Redux Toolkit + RTK Query
- Structure: feature-based components and slices

Typical feature structure:
- `features/auth/*`
- `features/board/*`
- `features/notifications/*`

## 3. Backend Architecture

Per service layering:
- routes/controllers: HTTP layer only (validation handoff, status codes, serialization)
- services: business logic and orchestration
- repositories: Prisma-based data access
- Prisma: schema + client
- PostgreSQL: persistent storage

### Communication
- REST APIs (`/api/v1/...`) for synchronous requests
- WebSocket channels for real-time task updates and online presence
- JSON request/response
- JWT-based auth for protected endpoints

## 4. Data Flow

### Authentication Flow (Registration/Login)
1. Frontend submits `POST /api/v1/auth/register`.
2. Gateway routes request to auth-service and applies rate limiting.
3. Auth service validates input and checks duplicate email.
4. Password is hashed with bcrypt (minimum 12 rounds).
5. User record saved with Prisma to PostgreSQL.
6. JWT is issued and stored in HTTP-only cookie.

### Task Update Flow
1. Frontend calls board endpoint (create/update/move task).
2. Board service validates payload and applies business rules.
3. Repository persists change via Prisma to PostgreSQL.
4. Board service emits WebSocket update event.
5. Connected clients update board state in near real-time.

## 5. Technology Stack (Locked)

- Language: TypeScript 5.x
- Runtime: Node.js 20.x
- Frontend: Next.js 14 + Tailwind CSS 3.x
- State Management: Redux Toolkit (RTK + RTK Query)
- Backend: Express.js 4.x
- Database: PostgreSQL 16
- ORM: Prisma 5.x
- Containers: Docker / Docker Compose
- CI/CD: GitHub Actions
- Logging: Winston

## 6. Deployment Standards

### Environments
- `dev`: local Docker Compose, fast iteration
- `staging`: QA validation before release
- `production`: self-hosted deployment behind Nginx reverse proxy

### CI/CD Pipeline (GitHub Actions)
1. Trigger on PR and merge to `main`.
2. Lint + type-check + tests.
3. Build services and Docker images.
4. Deploy to target environment.
5. Verify health endpoints and basic smoke checks.

### Rollback
- Revert to previous stable image/tag.
- Re-run deployment workflow with known-good version.

## 7. Key Performance and Security Targets

Performance targets:
- API response time: < 200 ms (95th percentile for core endpoints)
- Real-time update latency: < 500 ms client-to-client
- Board page load: < 2 seconds on standard broadband

Security targets:
- HTTPS only in non-local environments
- JWT in HTTP-only cookies
- bcrypt password hashing (12+ rounds)
- server-side input validation for all state-changing routes
- CSRF protection for auth and other state-changing operations
- no secrets/tokens/passwords in logs

## 8. AI Assistant Guardrails

- Do not propose stack substitutions (no NestJS, MongoDB, etc.).
- Preserve service boundaries; do not collapse services ad hoc.
- Use Prisma for DB operations, not raw SQL by default.
- Keep API contracts REST + JSON with explicit status codes.
