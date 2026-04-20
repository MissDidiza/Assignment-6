# AGILE_PLANNING.md — CampusFind: Smart Campus Lost & Found System
## Assignment 6: Agile User Stories, Backlog, and Sprint Planning

---

## 1. User Stories

User stories were derived directly from the functional requirements in Assignment 4 (FR-01 to FR-12) and the use cases in Assignment 5 (UC-01 to UC-08). Each story follows the format: *"As a [role], I want [action] so that [benefit]."* All stories satisfy the INVEST criteria (Independent, Negotiable, Valuable, Estimable, Small, Testable).

### Traceability Map

| User Story ID | Source Requirement (A4) | Source Use Case (A5) |
|---|---|---|
| US-001 | FR-01 | UC-01 |
| US-002 | FR-02 | UC-01 |
| US-003 | FR-03 | UC-02 |
| US-004 | FR-04 | UC-03 |
| US-005 | FR-05 | UC-04 |
| US-006 | FR-06 | UC-05 |
| US-007 | FR-07 | UC-06 |
| US-008 | FR-08 | UC-07 |
| US-009 | FR-09 | UC-08 |
| US-010 | FR-10 | UC-08 |
| US-011 | FR-11 | — |
| US-012 | FR-12 | — |
| US-013 | NFR-09 | — |
| US-014 | NFR-10 | — |

---

### User Stories Table

| Story ID | User Story | Acceptance Criteria | Priority |
|---|---|---|---|
| US-001 | As a **student**, I want to register an account using my university email so that I can access the CampusFind platform securely. | Registration blocked for non-university emails. Verification email sent within 60 seconds. Account inactive until email is verified. Duplicate emails rejected. | High |
| US-002 | As a **registered user**, I want to log in and log out securely so that my account and reports are protected from unauthorised access. | Login succeeds with correct credentials and issues a JWT (8-hour expiry). Login fails with a generic error for wrong credentials. Logout invalidates the session. | High |
| US-003 | As a **student**, I want to submit a lost item report with photos so that the system can attempt to find and match my lost item. | All mandatory fields enforced. Up to 3 photos accepted (max 5 MB each). Report saved and visible on dashboard within 3 seconds. AI matching job triggered within 30 seconds. | High |
| US-004 | As a **staff member or finder**, I want to submit a found item report quickly so that lost items can be reunited with their owners as fast as possible. | Report submission completed in under 2 minutes. Found report immediately visible to admin staff. AI matching job triggered within 30 seconds. | High |
| US-005 | As a **student**, I want the system to automatically compare my lost item report with found item reports so that I do not have to manually search through all reports myself. | AI matching completes within 60 seconds for up to 10,000 open reports. Matches above 70% confidence are surfaced. Confidence score shown to admin. | High |
| US-006 | As a **student**, I want to receive an email and in-app notification when a probable match is found for my lost item so that I am informed immediately without having to check the platform constantly. | Email delivered within 5 minutes of match detection. Email contains item name, confidence score, and a link to the match. In-app notification visible on next login. Students can opt out of emails. | High |
| US-007 | As a **campus admin**, I want to review AI-suggested matches side by side and confirm or dismiss them so that only accurate matches are acted upon. | Pending matches sorted by confidence score. Side-by-side view shows both reports with photos. Confirm updates both reports to "Matched." Dismiss is logged with admin ID and timestamp. | High |
| US-008 | As a **campus admin**, I want to manage a digital handover workflow so that item returns are recorded with a full audit trail and legal accountability. | Admin can set pickup location and time. Student receives notification with pickup details. Digital acknowledgment recorded with timestamp. Both reports updated to "Resolved" on confirmation. | High |
| US-009 | As a **campus admin**, I want to search and filter all lost and found reports by category, date, location, and status so that I can efficiently manage a large volume of reports. | Search results returned within 2 seconds for up to 50,000 reports. Filters can be combined. Results show item name, category, date, location, status, and thumbnail. | Medium |
| US-010 | As a **university administrator**, I want to view a statistics dashboard and export a CSV report so that I can report on item recovery rates to university management. | Statistics updated within 10 minutes of any status change. Filterable by date range. CSV export contains all fields with no personal data. | Medium |
| US-011 | As a **super admin**, I want the system to automatically archive resolved reports and delete personal data after 120 days so that the platform complies with POPIA data retention requirements. | Archiving job runs nightly at 02:00. Personal data removed after retention period. Anonymised tombstone record retained for statistics. Super admin receives daily summary email. | Medium |
| US-012 | As a **super admin**, I want to manage user roles and system configuration through the admin UI so that I can control access and adjust system behaviour without developer intervention. | Three roles enforced: Student, Admin, Super Admin. Role changes take effect within 60 seconds. All role change events logged in audit trail. HTTP 403 returned for unauthorised endpoint access. | Medium |
| US-013 | As a **system administrator**, I want all data transmitted between users and the server to be encrypted using HTTPS (TLS 1.2+) so that user data is protected from interception. | SSL Labs scan returns grade A or higher. All HTTP requests automatically redirected to HTTPS. Zero unencrypted endpoints in production. | High |
| US-014 | As a **system administrator**, I want all user passwords to be hashed using bcrypt (cost factor 12) so that plain-text passwords are never stored or exposed even in the event of a data breach. | bcrypt with cost factor >= 12 confirmed in code review. No plain-text passwords appear in logs. Penetration test confirms password storage compliance. | High |

---

## 2. Product Backlog

The backlog is prioritised using **MoSCoW** (Must-have, Should-have, Could-have, Won't-have). Effort is estimated using **Fibonacci story points** (1, 2, 3, 5, 8, 13) where:
- **1–2:** Simple, low-risk task (e.g., a form with validation)
- **3–5:** Moderate complexity (e.g., an API endpoint with business logic)
- **8–13:** High complexity (e.g., AI integration, async workflows)

### Prioritisation Justification

- **Must-have** stories are the core of the MVP — without them the system cannot function at all. They map directly to the highest-priority stakeholder concerns identified in Assignment 4 (students submitting reports, being notified of matches, and admins managing handovers).
- **Should-have** stories add significant value but the MVP can launch without them. They address admin efficiency and institutional reporting needs.
- **Could-have** stories are quality-of-life improvements that would be tackled in later sprints.
- **Won't-have** stories are explicitly out of scope for this semester (e.g., native mobile app, multi-campus support).

### Product Backlog Table

| Story ID | User Story Summary | MoSCoW | Story Points | Dependencies |
|---|---|---|---|---|
| US-001 | Student registers with university email | Must-have | 3 | None |
| US-002 | Secure login and logout with JWT | Must-have | 3 | US-001 |
| US-013 | HTTPS encryption for all data in transit | Must-have | 2 | None |
| US-014 | bcrypt password hashing | Must-have | 1 | US-001 |
| US-003 | Student submits lost item report with photos | Must-have | 5 | US-002 |
| US-004 | Finder submits found item report with photos | Must-have | 5 | US-002 |
| US-005 | AI matching engine compares lost and found reports | Must-have | 13 | US-003, US-004 |
| US-006 | Student receives match notification (email + in-app) | Must-have | 5 | US-005 |
| US-007 | Admin reviews and confirms AI match suggestions | Must-have | 5 | US-005, US-002 |
| US-008 | Digital handover workflow with audit trail | Must-have | 8 | US-007 |
| US-009 | Admin searches and filters all reports | Should-have | 3 | US-003, US-004 |
| US-010 | Statistics dashboard and CSV export | Should-have | 5 | US-008 |
| US-012 | Role-based access control (RBAC) | Should-have | 5 | US-002 |
| US-011 | Automated POPIA data archiving and deletion | Could-have | 5 | US-008 |

---

## 3. Sprint Planning

### Sprint 1 Goal

> **"Deliver a working authentication and report submission system so that students can register, log in, and submit lost and found item reports with photo uploads — forming the foundation of the CampusFind MVP."**

This sprint establishes the core data entry layer of the system. Without user accounts and report submission, no other feature (AI matching, notifications, handovers) can function. Completing this sprint means a real student could register and submit a report on a live deployment.

**Sprint Duration:** 2 weeks
**Sprint Number:** 1
**Team:** Individual developer (solo project)

---

### Selected User Stories for Sprint 1

| Story ID | User Story Summary | Story Points | Justification |
|---|---|---|---|
| US-013 | HTTPS encryption | 2 | Must be in place before any user data is transmitted |
| US-014 | bcrypt password hashing | 1 | Required before any account can be created securely |
| US-001 | Student registers with university email | 3 | Foundation — all other features require an account |
| US-002 | Secure login and logout with JWT | 3 | Required before any authenticated action can be taken |
| US-003 | Student submits lost item report with photos | 5 | Core value proposition for the student actor |
| US-004 | Finder submits found item report with photos | 5 | Core value proposition for the finder actor |

**Total Sprint Points: 19**

---

### Sprint 1 Backlog — Task Breakdown

| Task ID | User Story | Task Description | Assigned To | Estimated Hours | Status |
|---|---|---|---|---|---|
| T-001 | US-013 | Configure TLS certificate and enforce HTTPS redirect on the Express server | Developer | 2 | To Do |
| T-002 | US-014 | Implement bcrypt password hashing (cost factor 12) in the User Service module | Developer | 2 | To Do |
| T-003 | US-001 | Design and implement the PostgreSQL users table schema (id, name, email, password_hash, role, verified, consent_timestamp) | Developer | 2 | To Do |
| T-004 | US-001 | Build POST /auth/register API endpoint with email domain validation and duplicate check | Developer | 4 | To Do |
| T-005 | US-001 | Integrate SendGrid to send email verification link on registration | Developer | 3 | To Do |
| T-006 | US-001 | Build GET /auth/verify/:token endpoint to activate account on link click | Developer | 2 | To Do |
| T-007 | US-001 | Build registration form UI in React (name, email, password, consent checkbox) with client-side validation | Developer | 4 | To Do |
| T-008 | US-002 | Build POST /auth/login endpoint — validate credentials, issue JWT (8-hour expiry) | Developer | 3 | To Do |
| T-009 | US-002 | Build POST /auth/logout endpoint — invalidate token (add to Redis denylist) | Developer | 2 | To Do |
| T-010 | US-002 | Build login and logout UI in React with JWT storage in memory (not localStorage) | Developer | 3 | To Do |
| T-011 | US-002 | Implement Auth Middleware — validate JWT on all protected routes, return 401 if invalid | Developer | 2 | To Do |
| T-012 | US-003 | Design PostgreSQL reports table schema (id, user_id, type, item_name, category, description, location, date, photo_urls[], status, timestamps) | Developer | 2 | To Do |
| T-013 | US-003 | Build POST /reports/lost API endpoint with field validation and Cloudinary photo upload integration | Developer | 5 | To Do |
| T-014 | US-003 | Build lost item report submission form UI in React (all fields, photo uploader, progress indicator) | Developer | 5 | To Do |
| T-015 | US-003 | Build student dashboard UI showing list of own reports with status badges | Developer | 3 | To Do |
| T-016 | US-004 | Build POST /reports/found API endpoint (reuses report schema, type = FOUND) | Developer | 3 | To Do |
| T-017 | US-004 | Build found item report submission form UI in React | Developer | 4 | To Do |
| T-018 | US-003, US-004 | Write unit tests for Report Service (field validation, photo size check, status assignment) | Developer | 3 | To Do |
| T-019 | US-001, US-002 | Write unit tests for Auth Controller (registration validation, JWT issuance, login failure) | Developer | 3 | To Do |
| T-020 | All | Deploy Sprint 1 build to staging environment using Docker Compose | Developer | 2 | To Do |

**Total Estimated Hours: 59 hours**

---

### Sprint 1 Definition of Done

A user story is considered Done when:
- [ ] All acceptance criteria from the user story are met.
- [ ] Unit tests written and passing (minimum 70% coverage for the module).
- [ ] Code reviewed (self-review checklist completed for solo project).
- [ ] Feature deployed to the staging environment and manually verified.
- [ ] No critical or high-severity bugs outstanding.

---

### Sprint 1 Velocity Target

| Metric | Value |
|---|---|
| Total story points committed | 19 |
| Total estimated hours | 59 hours |
| Sprint duration | 2 weeks (10 working days) |
| Average hours per day | ~6 hours/day |
| Remaining sprints planned | Sprint 2 (AI matching + notifications), Sprint 3 (admin dashboard + handover + statistics) |