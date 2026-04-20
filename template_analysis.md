# template_analysis.md — CampusFind: Smart Campus Lost & Found System
## Assignment 7: GitHub Project Template Analysis and Selection

---

## 1. GitHub Project Templates — Comparison Table

GitHub Projects offers several pre-built templates for managing software development workflows. The four templates evaluated below are the most commonly used for Agile software projects.

| Feature | Basic Kanban | Automated Kanban | Bug Triage | Team Planning |
|---|---|---|---|---|
| **Default Columns** | To Do, In Progress, Done | To Do, In Progress, Done | Needs Triage, High Priority, Low Priority, Closed | To Do, In Progress, Done |
| **Number of Default Columns** | 3 | 3 | 4 | 3 |
| **Automation Features** | None — all card movement is manual | Issues auto-move to "In Progress" when a PR is opened. Issues auto-move to "Done" when PR is merged or issue is closed. | Issues auto-move to "Closed" when closed. No sprint automation. | Supports iteration (sprint) fields. Issues can be assigned to sprints automatically. |
| **GitHub Issues Integration** | Manual — drag cards or add issues manually | Full — linked issues trigger automatic column transitions | Partial — focuses on bug labels and priority fields | Full — supports milestones, iterations, and assignees |
| **WIP Limiting Support** | Not built-in | Not built-in | Not built-in | Not built-in (must be enforced manually) |
| **Custom Fields Support** | No | No | Priority field (High/Low) | Yes — iteration, priority, size, and custom fields |
| **Agile Methodology Fit** | Basic task tracking; no sprint support | Good for continuous delivery; limited sprint tracking | Suited for bug management, not feature development | Best fit for Scrum/Agile — supports sprints, story points, and team assignments |
| **Best Suited For** | Very small projects or personal to-do lists | CI/CD pipelines where PRs drive workflow | Maintenance phases with many bug reports | Active Agile development with sprints and a backlog |
| **Customisability** | Low | Medium | Low | High |
| **Complexity** | Very low | Low | Low | Medium |

---

## 2. Chosen Template: Automated Kanban (Customised)

### Chosen Template: **Automated Kanban**

After evaluating all four templates, the **Automated Kanban** template was selected as the foundation for the CampusFind project board, with significant customisation to add sprint tracking and QA workflow stages.

### Justification

**1. Automation reduces manual overhead for a solo developer.**
The most critical feature of the Automated Kanban template is that issues automatically move between columns based on GitHub events (pull requests opened → In Progress; issues closed → Done). As a solo developer, manually dragging cards across a board after every code push is friction that adds no value. The automation keeps the board accurate without extra effort.

**2. GitHub Issues integration is seamless.**
The Automated Kanban template is designed around GitHub Issues as its primary unit of work. In Assignment 6, all 14 user stories were defined as GitHub Issues. The Automated Kanban template allows those issues to be linked directly to board cards, preserving the traceability chain from Assignment 4 (requirements) → Assignment 5 (use cases) → Assignment 6 (user stories) → Assignment 7 (board tasks).

**3. It can be customised to add sprint and QA stages.**
While the default template only has three columns, custom columns (Backlog, Testing, Blocked, Review) can be added to model the full CampusFind development workflow. This gives the board the sprint-awareness of the Team Planning template while retaining the automation of the Automated Kanban template.

**4. It aligns with the CampusFind Agile workflow defined in Assignment 6.**
Sprint 1 was planned around a continuous delivery model — tasks move from To Do → In Progress as soon as a developer starts them, and to Done when the pull request is merged and the feature is verified. This maps directly to the Automated Kanban automation triggers.

**Why not Team Planning?**
The Team Planning template's strength is managing multiple team members across multiple sprints with iteration fields and story point tracking. For a solo developer on a single-semester project, this added complexity is unnecessary overhead. The Automated Kanban template provides 80% of the value with 20% of the complexity.

**Why not Basic Kanban?**
The complete absence of automation in Basic Kanban means the board would fall out of sync with actual development progress almost immediately. A board that does not reflect reality is worse than no board at all.

---

## 3. Custom Columns Added

The default Automated Kanban (To Do → In Progress → Done) was extended with the following custom columns to reflect the CampusFind development and QA workflow:

| Column | Purpose | WIP Limit |
|---|---|---|
| **Backlog** | All user stories and tasks not yet selected for the current sprint. Items sit here until sprint planning pulls them into To Do. | No limit |
| **To Do** | Tasks selected for the current sprint that have not yet been started. | 6 tasks |
| **In Progress** | Tasks actively being worked on right now. | 3 tasks |
| **Testing** | Tasks where code is complete but acceptance criteria have not yet been verified against the test cases defined in Assignment 5. | 3 tasks |
| **Blocked** | Tasks that cannot proceed due to a dependency, technical blocker, or unanswered question. Flagged for immediate attention. | No limit (any card here is urgent) |
| **Done** | Tasks where code is merged, acceptance criteria verified, and the feature is deployed to staging. | No limit |