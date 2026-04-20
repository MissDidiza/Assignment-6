# kanban_explanation.md — CampusFind: Smart Campus Lost & Found System
## Assignment 7: Kanban Board Definition and Explanation

---

## 1. What is a Kanban Board?

A Kanban board is a visual project management tool that represents the flow of work through a series of stages, typically displayed as columns. Each unit of work — a task, user story, or bug — is represented as a card that moves from left to right across the board as it progresses through the workflow, from not started to completed.

The word "Kanban" comes from Japanese and translates roughly to "visual signal" or "card." It originated in Toyota's manufacturing system in the 1940s as a way to manage production flow and reduce waste. In software development, Kanban was popularised by David J. Anderson in the 2000s and has since become one of the most widely used Agile workflow management approaches in the industry.

The three core principles of Kanban are:
- **Visualise the workflow** — make all work and its current state visible to everyone on the team.
- **Limit work-in-progress (WIP)** — cap the number of tasks in each stage to prevent bottlenecks and context-switching.
- **Manage flow** — continuously monitor and improve how work moves through the system.

---

## 2. The CampusFind Kanban Board

### 2.1 Board Structure

The CampusFind Kanban board is hosted on GitHub Projects and uses a customised Automated Kanban template. It consists of six columns representing the full lifecycle of a development task:

```
| Backlog | To Do | In Progress | Testing | Blocked | Done |
```

Each card on the board represents either a user story (linked to a GitHub Issue from Assignment 6) or a sub-task broken down from the Sprint 1 task table in Assignment 6. Cards are labelled with one of the following GitHub labels:

- `feature` — a new user-facing capability (e.g., US-003: Submit Lost Item Report)
- `security` — a security or compliance task (e.g., US-013: HTTPS encryption)
- `infrastructure` — a deployment or configuration task (e.g., T-020: Docker deployment)
- `testing` — a test-writing task (e.g., T-019: Auth unit tests)
- `blocked` — any card that cannot proceed (applied in addition to other labels)

---

### 2.2 How the Board Visualises Workflow

Each column on the CampusFind board represents a distinct stage in the development lifecycle:

- **Backlog** holds all user stories and tasks that are defined but not yet selected for the current sprint. Looking at this column gives an immediate picture of how much planned work remains in the project.
- **To Do** contains only the tasks selected for Sprint 1. The column cap of 6 tasks means at any given time, the sprint scope is visible at a glance — there is no ambiguity about what this sprint is trying to deliver.
- **In Progress** shows what is actively being worked on right now. The WIP limit of 3 prevents the developer from starting too many things simultaneously and losing focus.
- **Testing** is the column that most basic Kanban templates omit. For CampusFind, a task is not done when the code is written — it is done when the acceptance criteria from Assignment 5 have been verified. The Testing column makes this verification step explicit and prevents tasks from jumping straight from In Progress to Done without quality checks.
- **Blocked** is a high-visibility column for tasks that cannot proceed. On a real team, any card in Blocked would be discussed in the daily standup immediately. As a solo developer, seeing a card in Blocked is a prompt to either solve the blocker or re-sequence the sprint work.
- **Done** is the final stage. A card only reaches Done when: code is merged, acceptance criteria verified, and the feature is live on the staging environment.

The automation built into the Automated Kanban template handles two transitions automatically:
- When a pull request linked to an issue is **opened** → the issue card moves from To Do to **In Progress**.
- When the pull request is **merged** (or the issue is **closed**) → the card moves to **Done**.

This means the board stays accurate without manual intervention during active development.

---

### 2.3 How the Board Limits Work-in-Progress (WIP)

WIP limits are one of the most important — and most commonly ignored — features of Kanban. Without WIP limits, it is easy to start every task in the sprint on day one and have none of them finished by the end of the sprint. WIP limits force a "finish before you start" discipline.

The CampusFind board enforces the following WIP limits:

| Column | WIP Limit | Rationale |
|---|---|---|
| To Do | 6 | Caps sprint scope to a manageable, committed set of tasks |
| In Progress | 3 | Prevents context-switching across too many concurrent tasks |
| Testing | 3 | Ensures testing keeps pace with development |
| Blocked | No limit | Blocked cards are urgent by definition — limiting them would hide problems |

If the In Progress column reaches its limit of 3, no new task can be started until one of the 3 current tasks moves to Testing or Done. This constraint feels counterintuitive at first — it seems like it slows things down. In practice it speeds things up, because it forces completion of existing work before new work begins, which reduces the cognitive overhead of context-switching and produces a steadier flow of finished features.

---

### 2.4 How the Board Supports Agile Principles

The CampusFind Kanban board supports the following core Agile principles from the Agile Manifesto:

**Working software over comprehensive documentation.**
The board's Definition of Done (code merged + acceptance criteria verified + deployed to staging) ensures that "Done" always means working software, not just completed paperwork.

**Responding to change over following a plan.**
The Backlog column can be re-prioritised at any time without disrupting the current sprint. If a new requirement emerges (e.g., a stakeholder requests a password strength indicator), a new card can be added to the Backlog and pulled into the next sprint without disrupting Sprint 1.

**Continuous delivery of valuable software.**
The board's flow model (Backlog → To Do → In Progress → Testing → Done) is designed so that individual features can be completed and deployed independently. The student registration feature (US-001) can go live before the AI matching engine (US-005) is built.

**Simplicity — the art of maximising the amount of work not done.**
The WIP limits and the explicit Blocked column make bottlenecks visible immediately, which creates pressure to resolve them quickly rather than letting blocked work pile up silently.

---

## 3. Kanban Board Setup Instructions (GitHub)

To recreate the CampusFind Kanban board on GitHub:

1. Go to the CampusFind GitHub repository.
2. Click the **Projects** tab → **New Project**.
3. Select **Automated Kanban** template.
4. Rename the project to `CampusFind Sprint Board`.
5. Add the following custom columns (in order): `Backlog`, `To Do`, `In Progress`, `Testing`, `Blocked`, `Done`.
6. Go to **Issues** → create a new issue for each user story (US-001 to US-014) from Assignment 6. Apply appropriate labels (`feature`, `security`, `infrastructure`, `testing`).
7. Add all US-001 to US-006 issues to the **To Do** column (Sprint 1 scope).
8. Add US-007 to US-014 to the **Backlog** column (future sprints).
9. Add individual task cards (T-001 to T-020) from Assignment 6 as sub-tasks linked to their parent issues.
10. Set column WIP limit notes in the column description field.