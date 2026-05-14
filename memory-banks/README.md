# Memory Banks - Personal Task Board (mrello)

## Purpose
This memory bank provides persistent context for AI assistants working on Taskboard/mrello in Module 03.

It captures architecture, coding conventions, domain language, and development workflows so AI output stays aligned with project standards.

This is a documentation/specification context package, not a full implementation repository.

## Structure

### architecture/
System architecture pattern, stack versions, service boundaries, data flow, deployment standards.

### conventions/
Coding standards, API/data conventions, naming, testing, error handling, and quality gates.

### domain/
Project-specific terms, personas, and business rules from PRD/epics/stories.

### workflows/
Development lifecycle from spec to production, including branching, PR, CI/CD, and rollback.

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
- `architecture/overview.md`: architecture pattern, services, data flow, deployment, targets
- `conventions/coding-standards.md`: coding, API/data, security, testing, DoD
- `domain/glossary.md`: project terms, personas, business rules
- `workflows/development-process.md`: delivery process from PRD to deployment
- `memory-bank-impact.md`: before/after AI quality comparison
- `IMPROVEMENTS.md`: peer-review feedback and refinement log

## AI Assistant Usage
When generating code or docs for this project:
1. Load architecture first for stack/runtime constraints.
2. Apply coding/API/data/security/testing rules from conventions.
3. Use glossary terms and business rules exactly as defined.
4. Follow workflow checklists before considering work complete.

For authentication stories, always align to STORY-001.01 rules (bcrypt 12+, JWT in HTTP-only cookies, Prisma + PostgreSQL, validation, tests).

## Maintenance
- Update when PRD/epics/stories or architecture standards change.
- Keep concise, specific, and action-oriented.
- Review after each major milestone.

**Last Updated:** 2026-05-14
**Version:** 1.0
