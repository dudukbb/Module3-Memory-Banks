# Coding Standards - Personal Task Board (mrello)

## 0. Core Rule

- TypeScript-first: all frontend and backend production code must be TypeScript.

## 1. Naming Conventions

- Variables/functions: `camelCase`
- React components/types/classes: `PascalCase`
- Constants/env keys: `UPPER_SNAKE_CASE`
- Files:
	- React components: `PascalCase.tsx`
	- Config/helper files: `kebab-case.ts` when applicable
	- Service/repository modules: `camelCase.ts` (keep consistent by package)
- API resources: plural nouns, lowercase (`/api/v1/users`, `/api/v1/tasks`)
- Database tables/columns: `snake_case`

## 2. Monorepo File Organization

- `apps/web`: Next.js frontend
- `apps/gateway`: API gateway
- `apps/auth-service`: authentication service
- `apps/board-service`: board and task operations
- `apps/notification-service`: email and reminders
- `packages/shared`: shared types and utilities

## 3. TypeScript & Structure

- Strict TypeScript required for APIs, entities, DTOs, and Redux slices.
- Keep backend layering: Routes -> Services -> Repositories -> Prisma.
- Keep frontend feature-based structure and reusable UI components.
- Prefer small, focused functions and single-responsibility modules.

### Backend Layer Rules
- Routes/controllers only handle HTTP concerns (request parsing, response codes, auth middleware hooks).
- Services contain business logic and orchestration.
- Repositories are the only layer accessing Prisma/database directly.

## 4. API Standards (REST)

- Base path: `/api/v1`.
- HTTP usage:
	- `GET` read
	- `POST` create
	- `PUT/PATCH` update
	- `DELETE` remove
- Use standard status codes: `200`, `201`, `204`, `400`, `401`, `403`, `404`, `409`, `422`, `500`.
- JSON-only payloads unless explicitly documented otherwise.

### Success Response Format
```json
{
	"success": true,
	"data": {},
	"meta": {
		"requestId": "uuid"
	}
}
```

### Error Response Format
```json
{
	"statusCode": 400,
	"message": "Validation failed",
	"error": "VALIDATION_ERROR",
	"details": {
		"field": "email"
	}
}
```

## 5. Validation Rules

- Validate all request bodies, params, and query values.
- Enforce required fields and type checks at API boundary.
- Return field-level validation details in error responses.
- Mirror key validations on frontend for UX; backend remains source of truth.

## 6. Data Standards

- PostgreSQL 16 is source of truth.
- Prisma 5 is required for data access and migrations.
- Use UUID/ID keys consistently per schema; enforce FK constraints.
- Use timestamps (`created_at`, `updated_at`) for auditable entities.
- Auth data rules:
	- Store `password_hash`, never plaintext password.
	- Use bcrypt (12+ rounds).

## 7. Security Rules

- Never log passwords, tokens, cookie values, or secrets.
- Password hashing must use bcrypt with minimum 12 rounds.
- JWT must be set/validated via HTTP-only cookies.
- Input validation is mandatory on all state-changing endpoints.
- CSRF protection is required for authentication and mutable operations.
- Use HTTPS-only assumptions for deployed environments.

## 8. Logging Rules

- Use Winston for backend structured logs.
- Required fields: timestamp, level, service, message, requestId (when available).
- Error logs must include stack trace in non-production-safe form.

## 9. Testing Requirements

- Unit tests: Jest
- API integration tests: Supertest
- E2E tests: Playwright
- Minimum coverage: 80% overall; critical auth flows should exceed baseline.

## 10. Pull Request and Code Review Checklist

### PR Checklist
- [ ] Story acceptance criteria mapped to changes
- [ ] Lint, type-check, tests passing
- [ ] New/changed endpoints documented
- [ ] Security-sensitive changes called out

### Code Review Checklist
- [ ] Layering respected (route/service/repository)
- [ ] Naming and file conventions followed
- [ ] Validation and error handling present
- [ ] Security rules applied (bcrypt/JWT/cookies/CSRF)
- [ ] Tests cover new behavior

## 11. Definition of Done

- Requirements implemented according to story acceptance criteria.
- Unit/integration/E2E tests updated and passing.
- Coverage threshold met (>= 80%).
- No lint/type errors.
- Docs/specs/memory-bank entries updated if behavior changed.

## 12. AI Assistant Rules

- Generate code aligned to this stack only.
- Follow existing naming and folder patterns before introducing new ones.
- Include validation and error handling by default.
- For auth stories, include secure hashing and token/session handling.
