# Memory Bank Improvements

## Feedback Received
- Include WebSocket and Nginx deployment details in architecture notes.
- Add stricter security/testing expectations in coding standards.
- Expand glossary with persona/business-rule terms used in PRD.
- Make impact report explicitly compare prompts without vs with memory banks.

## Changes Made
- Updated architecture with required services, REST + WebSocket communication, auth/task data flows, Nginx, CI/CD, and targets.
- Updated coding standards with backend layering, API formats, CSRF/security rules, Winston logging, Jest/Supertest/Playwright, and 80% coverage target.
- Expanded glossary to include Taskboard/mrello terms, personas (Sarah/Mike/Alex), and required MVP business rules.
- Updated workflow with full PRD-to-deployment sequence, branching model, and maintenance workflow.
- Revised impact analysis for STORY-001.01 with explicit prompt comparison and correction-time estimates.

## Future Improvements (Next Iteration)
- Add role-specific playbooks under `roles/` for developer, QA, and PM.
- Add endpoint-level examples for auth, tasks, and notifications.
- Add a concise troubleshooting guide for CI failures and deployment rollback checks.
