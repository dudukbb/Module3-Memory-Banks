# Memory Banks - Personal Task Board (mrello)

## Purpose
This memory bank provides persistent project context for AI assistants working on Personal Task Board (mrello) in Module 03.

It captures architecture, coding conventions, domain language, and delivery workflows so AI-generated outputs remain consistent with project standards.

This repository focuses on AI context engineering and memory banks. It is a documentation/specification support package, not a full product implementation repository.

## Structure

### architecture/
System architecture pattern, stack versions, service boundaries, data flow, and deployment standards.

### conventions/
Coding standards, API/data conventions, naming, testing requirements, error handling, and quality gates.

### domain/
Project-specific terms, personas, and business rules derived from PRD, epics, and stories.

### workflows/
Development lifecycle from specification to production, including branching, PR flow, CI/CD, and rollback.

### roles/
Role-specific context (developer, QA, PM) for future extension.

## Quick Navigation
- [Architecture Overview](architecture/overview.md)
- [Coding Standards](conventions/coding-standards.md)
- [Domain Glossary](domain/glossary.md)
- [Development Process](workflows/development-process.md)
- [Memory Bank Impact](memory-bank-impact.md)
- [Improvements](IMPROVEMENTS.md)

## Folder Map
- `architecture/overview.md`: architecture pattern, services, data flow, deployment, and performance/security targets
- `conventions/coding-standards.md`: coding standards, API/data rules, security, testing, and Definition of Done
- `domain/glossary.md`: project terminology, personas, and business rules
- `workflows/development-process.md`: delivery process from PRD to deployment
- `memory-bank-impact.md`: measurable before/after AI output comparison
- `IMPROVEMENTS.md`: peer-review feedback and refinement history

## AI Assistant Usage
When generating code or documentation for this project:
1. Load architecture first for stack/runtime constraints.
2. Apply coding, API/data, security, and testing rules from conventions.
3. Use glossary terminology and business rules exactly as defined.
4. Follow workflow checklists before considering work complete.

For authentication stories, align to STORY-001.01 requirements (bcrypt 12+, JWT in HTTP-only cookies, Prisma + PostgreSQL, validation, and tests).

## Maintenance
- Update when PRD, epics, stories, or architecture standards change.
- Keep entries concise, specific, and action-oriented.
- Review after each major milestone.

**Last Updated:** 2026-05-14
**Version:** 1.0
