# REFLECTION_A6.md — Challenges in Agile Planning as a Solo Developer
## CampusFind: Smart Campus Lost & Found System — Assignment 6

---

## Overview

Agile methodology was designed for teams. Scrum defines distinct roles — Product Owner, Scrum Master, and Development Team — that are played by different people precisely because the tensions between those roles produce better outcomes. The Product Owner pushes for more features. The Development Team pushes back on unrealistic estimates. The Scrum Master facilitates the negotiation. As a solo developer on CampusFind, all three of those roles collapse into one person, and that creates a unique and often uncomfortable set of challenges. This reflection documents the internal resistance and difficulty experienced while completing this assignment.

---

## Challenge 1: The Prioritisation Paralysis

The hardest part of creating the product backlog was not deciding what was Most-have — that was obvious. The hard part was deciding what was Should-have versus Could-have, and especially what to put in the Won't-have category. Every feature in the system exists because a stakeholder needs it. When you are both the Product Owner (who represents stakeholders) and the Development Team (who has to actually build it), there is a strong psychological pull to include everything in the Must-have category.

Writing "Won't-have: native mobile app, multi-campus support, real-time push notifications" felt like a failure — like I was letting the stakeholders down. But the discipline of MoSCoW prioritisation forced me to confront a basic truth: a feature that is planned but never built because the developer ran out of time is worse than a feature that is explicitly deferred. Being honest about scope protects the project from the most common failure mode in solo development, which is starting too many things and finishing none of them.

The resolution was to apply a strict test to every story: "Could the system deliver real value to a real student without this feature?" If yes, it was not Must-have. This test cut the Must-have list from 14 stories to 9, which was uncomfortable but honest.

---

## Challenge 2: Estimating Without a Team

Story point estimation in Scrum is designed to be a team activity — Planning Poker exists because different people have different knowledge and different blind spots, and the discussion that emerges when estimates disagree is where the most important information surfaces. As a solo developer, there is no one to disagree with.

The specific difficulty I encountered was estimating US-005 (AI matching engine). My first instinct was to give it 5 story points because I already knew which libraries to use (sentence-transformers, MobileNetV2). But when I broke it down into tasks, I realised the complexity was hidden in the integration work: setting up the FastAPI microservice, connecting it to the Redis job queue, handling timeouts and retries, and writing meaningful tests for a probabilistic system. I revised it to 13 points — the highest on the Fibonacci scale I was using.

This experience revealed that solo estimation tends to be optimistic because there is no one to ask "but what about the error handling?" or "how are you going to test that?" The discipline of breaking every story into concrete tasks before finalising the estimate was the closest I could get to replicating the value of team-based estimation.

---

## Challenge 3: Sprint Scope — The Tension Between Ambition and Reality

When selecting stories for Sprint 1, my first draft included US-005 (AI matching engine) because I was excited about it — it is the most technically interesting part of the system. But US-005 depends on US-003 and US-004 (report submission), which depend on US-001 and US-002 (authentication). Including US-005 in Sprint 1 would mean building the entire foundation of the system and the most complex feature simultaneously in two weeks.

The Scrum principle of delivering a potentially shippable product increment at the end of every sprint resolved this conflict. At the end of Sprint 1, is a system with authentication, report submission, and AI matching "potentially shippable"? No — because there are no notifications, no admin interface, and no handover workflow. A student could submit a report but would never be told if it was matched. That is not a usable product increment.

Removing US-005 from Sprint 1 and focusing purely on authentication and report submission was the right call — but it required accepting that the "exciting" work would come in Sprint 2, and that Sprint 1 would feel unglamorous. This is a discipline that is easy to understand intellectually and surprisingly difficult to follow in practice.

---

## Challenge 4: Traceability as a Solo Developer

The assignment requires traceability between user stories (Assignment 6), use cases (Assignment 5), functional requirements (Assignment 4), and the system specification (Assignment 3). Maintaining this traceability across four assignments over several weeks is straightforward when working in a team with shared documentation tools. As a solo developer working across multiple sessions, it required going back and re-reading all three prior assignments carefully before writing a single user story.

The traceability map at the top of AGILE_PLANNING.md was built last, not first — and building it revealed one gap: there was no user story directly covering the student's ability to view and update their own report after submission (which was FR-06 in Assignment 4 and UC-05 in Assignment 5). This was absorbed into US-003's acceptance criteria rather than becoming a standalone story, but it was a near miss. In a team environment, a product owner or business analyst would likely have caught this earlier.

---

## Conclusion

Agile is fundamentally a social methodology adapted here for individual use, and the friction that creates is instructive. The resistance I felt when cutting scope, the difficulty of estimating without a team, the temptation to include exciting features in Sprint 1 — all of these are the same pressures that real Scrum teams navigate through structured ceremonies and role separation. Experiencing them alone, with only internal discipline as the check, gave me a much deeper appreciation for why those ceremonies exist. They are not bureaucracy — they are the mechanisms that prevent the very specific failure modes that this assignment forced me to confront personally.