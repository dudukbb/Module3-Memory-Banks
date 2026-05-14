# Domain Glossary - Personal Task Board (mrello)

## Taskboard / mrello
**Definition:** Internal task management web app for small software teams.
**Context:** Primary product described in PRD and epics.
**Example:** "Taskboard centralizes team task status in one place."

## mrello
**Definition:** Project codename used for the Taskboard implementation repository and standards.
**Context:** Architecture and coding standards reference this name.

## Kanban Board
**Definition:** Visual workflow board with status-based columns.
**Context:** Core UI pattern for task management.
**Example:** "Move task from To Do to In Progress on the Kanban board."

## Task
**Definition:** Unit of work tracked by the team.
**Context:** Main business entity with title, status, assignee, and due date.

## Task Card
**Definition:** Individual work item with title, description, assignee, status, and due date.
**Relationships:** Belongs to a board and a status column.
**Example:** "The card includes assignee avatar and due date indicator."

## Task Status
**Definition:** Current lifecycle state of a task.
**Context:** Drives board column placement and workflow visibility.

## To Do
**Definition:** Status for tasks not yet started.
**Context:** Default status for new tasks.

## In Progress
**Definition:** Status for tasks actively being worked on.
**Context:** Indicates ongoing implementation.

## Done
**Definition:** Status for completed tasks.
**Context:** End state in MVP workflow.

## Assignee
**Definition:** Team member responsible for a task.
**Context:** Used for ownership clarity, filtering, and notifications.

## Due Date
**Definition:** Target completion date/time for a task.
**Context:** Used by reminders and planning.

## Priority
**Definition:** Relative urgency/importance indicator for a task.
**Context:** Helps ordering and attention management.

## Real-Time Sync
**Definition:** Automatic propagation of task/board changes across connected clients.
**Context:** Key productivity requirement from PRD.

## Online Presence
**Definition:** Visibility of users currently active on the board.
**Context:** Supports coordination and awareness.

## Notification Preferences
**Definition:** User-level settings for notification channels and event types.
**Context:** Controls assignment/status/reminder notifications.

## Password Reset Token
**Definition:** Time-limited token used to securely reset a user password.
**Context:** Part of auth-service password reset flow.
**Example:** "User receives reset link containing token valid for 1 hour."

## JWT Session
**Definition:** Auth mechanism using JSON Web Tokens and secure cookies/tokens.
**Context:** Required for protected board access.

## Small Engineering Team
**Definition:** Target team size for this product (roughly 2-5 developers).
**Context:** Explains design preference for lightweight workflows.

## Persona: Sarah
**Definition:** Primary developer persona from PRD.
**Context:** Needs fast updates, low-friction interactions, and clear ownership visibility.

## Persona: Mike
**Definition:** Team lead persona from PRD.
**Context:** Needs high-level status visibility and bottleneck detection.

## Persona: Alex
**Definition:** New team member persona from PRD.
**Context:** Needs quick onboarding and clear work context.

---

## Key Business Rules

### BR-01: Single Shared Board for MVP
**Rule:** MVP supports one shared board per team.
**Rationale:** Keep scope focused and onboarding simple.

### BR-02: Fixed Three-Column Workflow for MVP
**Rule:** Task statuses are fixed to To Do, In Progress, and Done.
**Rationale:** Avoid workflow complexity in initial release.

### BR-03: Assignment Limited to Registered Users
**Rule:** Tasks can only be assigned to users with valid registered accounts.
**Rationale:** Ensure ownership and notification reliability.

### BR-04: Password Reset Token Expiration
**Rule:** Password reset tokens expire after 1 hour.
**Rationale:** Reduce token abuse risk.

### BR-05: Real-Time Update Latency Target
**Rule:** Real-time updates should appear for connected clients within 500 ms.
**Rationale:** Maintain collaboration flow and trust in board accuracy.

### BR-06: Due Date Reminder Timing
**Rule:** Due date reminder notifications are sent 24 hours before deadline.
**Rationale:** Provide actionable notice without notification fatigue.
