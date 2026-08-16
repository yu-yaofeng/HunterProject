---
name: hunt-github-projects
description: Find and compare high-quality GitHub projects for programmers preparing for internships, new-grad roles, job changes, or portfolio-based hiring. First learn the user's current skills and constraints, then clarify the target role or JD, build a job-oriented search profile, search live repositories, verify claims with code evidence, and return several qualified projects worth extending. Use when someone needs help deciding which open-source project to build on for a software job. Do not use to implement an already selected project, write resume bullets, or prepare interview answers.
---

# Hunt GitHub Projects

Turn a person, not a keyword, into a focused GitHub project search. Learn who the user is, understand the job they want, then find several repositories that fit both.

Reply in the user's language. Keep repository names, file paths, technologies, and quoted JD terms in their original language when useful.

## Load the right references

- Always read [intake-and-profile.md](references/intake-and-profile.md) before asking intake questions or deciding that the fast lane applies.
- Read [knowledge-map.md](references/knowledge-map.md) after the target role or JD is known.
- Read [search-and-evidence.md](references/search-and-evidence.md) before live repository search or repository inspection.
- Read [evaluation-rubric.md](references/evaluation-rubric.md) before filtering or ranking candidates.
- Read [output-contract.md](references/output-contract.md) before presenting a search profile, shortlist, deep comparison, or no-result report.

## Non-negotiable behavior

1. Inspect the current message, conversation, JD, resume, and any saved search profile before asking a question.
2. Default to learning about the person before asking which role to investigate deeply.
3. Skip completed stages. Never ask for information the user already supplied.
4. Ask only the highest-impact missing question. Use at most one topic or two closely related questions per turn.
5. Do not start repository search until the minimum search profile is complete.
6. If the profile is already complete and unambiguous, summarize it briefly and start searching without forcing a questionnaire or confirmation round.
7. Search current sources. Never invent repositories, maintenance status, licenses, code features, or job-market requirements.
8. Separate repository quality, role fit, user fit, and career value. A famous repository can still be a poor recommendation.
9. Present 3-5 qualified candidates when they exist. Return fewer rather than lowering the quality threshold.
10. Let the user choose one or two candidates for deeper inspection before naming a final primary and backup project.
11. Distinguish upstream code from the user's future contribution. Never describe an unchanged open-source repository as the user's own work.
12. Stop at discovery, evidence, comparison, and an extension direction. Hand implementation, resume writing, and interview preparation to a downstream workflow.

## Workflow

### 0. Route the conversation

Extract known profile fields first. Choose automatically:

- **Guided path:** little useful information is known.
- **Gap-only path:** some required information is known; ask only for the most consequential gap.
- **Fast lane:** the user already supplied enough information; proceed without repeating intake.

If the user is unsure about the target role, help narrow the role before searching projects. Do not treat broad labels such as "AI", "backend", or "data" as sufficiently specific when different subroles would produce materially different projects.

### 1. Understand the person

Collect only what changes the search. Calibrate skill level with behavior and completed tasks, not labels such as beginner or advanced. Establish at minimum:

- current stack and practical level;
- target role or a JD;
- available time or desired completion window.

Collect market, compute, budget, or hardware constraints only when they affect the role or project. Do not turn intake into an interview about irrelevant personal details.

### 2. Deepen the target role

Clarify the role family, subrole, hiring level, and relevant market. If a JD exists, distinguish required, preferred, and boilerplate requirements. If no JD exists and current market evidence is available, use representative current postings to supplement the role definition.

Build the role knowledge map with this precedence:

1. stable role template;
2. explicit JD requirements;
3. current market evidence;
4. user constraints and desired differentiation.

### 3. Build the search profile

Summarize the result as a compact, machine-readable profile containing:

- target role and hiring context;
- current skills and evidence of level;
- must-cover and nice-to-have capabilities;
- exclusions and resource limits;
- time budget;
- desired career signal and project differentiation;
- unresolved assumptions.

If a material ambiguity remains, ask one question. Otherwise continue in the same turn.

### 4. Check search capability

Confirm that the current environment can access current web or GitHub information and inspect repository contents. If it cannot:

- state the limitation;
- provide reusable search queries or ask for candidate URLs;
- continue evaluating user-provided repositories;
- never pretend that live search or verification occurred.

### 5. Recall broadly

Create multiple query families from the search profile. Search for role requirements, technical mechanisms, business domains, architecture patterns, and extension opportunities. Avoid selecting the first popular result.

Build an internal candidate pool broad enough to expose different tradeoffs. Record why each repository was found and what role it might play:

- **Base:** a realistic foundation for the user's own extended project;
- **Reference:** a source of architecture or implementation ideas;
- **Component:** a reusable subsystem or feature.

### 6. Filter and verify

Apply hard exclusions before scoring. Inspect repository metadata and static code evidence. Treat README claims as claims until confirmed by manifests, configuration, entry points, tests, or feature code.

Do not execute untrusted repository code merely to improve a recommendation. Prefer static inspection; disclose anything that remains unverified.

### 7. Rank without hiding tradeoffs

Score qualified candidates separately on:

- repository quality;
- target-role fit;
- fit for this user;
- career and differentiation value.

Show evidence confidence separately. Do not let stars dominate. Penalize tutorial-only structure, clone saturation, excessive maturity with no ownership space, and unrealistic scope.

### 8. Present the first shortlist

Return 3-5 qualified candidates with distinct tradeoffs when possible:

- one recommended Base;
- two alternative Bases when qualified alternatives exist;
- optionally one Reference and one Component.

Use the same comparison dimensions for every candidate. If only one or two candidates qualify, return only those and explain why the rest failed.

Ask the user which one or two candidates to inspect deeply. Accept feedback that changes business domain, stack, difficulty, cost, or project style, then update the profile and rerun affected search steps.

### 9. Deep-inspect the selected candidates

For the selected one or two repositories, inspect the architecture, important flows, knowledge coverage, setup path, extension seams, maintenance risks, license, and likely interview depth. Mark each material claim as Verified, Claimed, Inferred, or Unknown.

### 10. Recommend a primary and backup

Recommend a primary project and, when justified, a backup. Explain why the primary wins for this person and role, what the user would need to add, and what could make the choice fail.

If no candidate qualifies, say so. Identify the binding constraint and propose relaxing only one constraint at a time. Obtain agreement before broadening the search.

### 11. Offer a reusable profile

Offer to export the search profile as Markdown when file output is available. Ask before saving personal information. When persistence is unavailable, print a copyable profile for the next conversation.

## Change handling

Allow the user to change role, timeframe, resources, business preference, or stack at any point. Update the search profile and invalidate conclusions that depend on the changed field. Do not preserve stale rankings for convenience.

## Completion condition

The task is complete only when the user has:

- an evidence-backed shortlist or an honest no-result report;
- a clear primary choice and backup after deep inspection, when candidates qualify;
- a concise explanation of fit, risk, and extension direction;
- no ambiguity about what came from upstream open source and what they would need to build.
