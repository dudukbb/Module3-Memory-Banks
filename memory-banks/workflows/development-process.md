# Development Process - Personal Task Board (mrello)

## 1. From Idea to Production Workflow

1. PRD
2. Epics
3. User stories
4. Implementation tasks
5. Development
6. Testing
7. Pull request
8. Review
9. CI/CD
10. Deployment

## 2. Branching Strategy

- Main branch: `main`
- Branch naming:
	- `feature/*`
	- `bugfix/*`
	- `hotfix/*`
- `main` is protected and requires PR + passing checks.

## 3. Pull Request Checklist

- [ ] Story acceptance criteria mapped to implementation
- [ ] Lint and type-check pass
- [ ] Tests pass locally
- [ ] Docs/spec updates included when needed
- [ ] Security-sensitive changes noted (auth, cookies, validation)
- [ ] Migration impact documented (if Prisma schema changed)

## 4. Code Review Checklist

- [ ] Follows coding standards and naming conventions
- [ ] Uses stack and architecture standards correctly
- [ ] Handles validation/errors explicitly
- [ ] Avoids security regressions
- [ ] Keeps scope aligned to story
- [ ] Includes/updates tests for changed behavior

## 5. Testing Strategy

- Unit tests: Jest
- Integration tests: Supertest
- E2E tests: Playwright

Coverage guidance:
- Minimum 80% overall coverage
- Auth and core task flows are priority coverage areas

## 6. Deployment Process

### CI/CD (GitHub Actions)
1. Build Docker images.
2. Run GitHub Actions pipeline (lint, type-check, tests, build).
3. Deploy to target environment.
4. Execute health checks and smoke checks.
5. Promote or stop based on checks.

### Rollback
- Re-deploy previous stable Docker tag.
- Confirm health endpoints and critical user flows.

## 7. Memory Bank Maintenance Workflow

1. Update memory files when PRD/epics/stories change.
2. Sync architecture/conventions after stack or process updates.
3. Re-run before/after impact test for major changes.
4. Log refinements in `memory-bank-impact.md` and `IMPROVEMENTS.md`.
5. Review memory bank quality each milestone.

## 8. AI Assistant Execution Notes

- Start each task with related PRD/epic/story context.
- Use memory-banks files as default project context.
- Keep generated changes small, testable, and traceable to acceptance criteria.
