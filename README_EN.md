<div align="center">

# HunterProject

**Find code-verified GitHub projects worth extending for a job search, based on personal background and a JD.**

[中文](README.md) | **English**

![version](https://img.shields.io/badge/version-v0.1.0-44cc11?style=flat-square)
![license](https://img.shields.io/badge/license-MIT-2094f3?style=flat-square)
![audience](https://img.shields.io/badge/audience-Software%20Job%20Seekers-f28c45?style=flat-square)
![workflow](https://img.shields.io/badge/workflow-Discover--Verify--Choose-a500a5?style=flat-square)

</div>

---

> First understand what kind of programmer the user wants to become, then find open-source GitHub projects that fit the job search and leave meaningful room for extension.

HunterProject helps programmers discover, verify, and compare open-source projects worth extending for a job search. It changes the interaction from “keyword in, repository out” to:

```text
personal background
→ target role or JD
→ role knowledge map
→ search profile
→ live GitHub project discovery
→ code-evidence verification
→ 3–5 qualified candidates
→ user selects 1–2 for deep inspection
→ primary and backup project recommendations
```

## Why it exists

Many developers know that GitHub contains high-quality projects but do not know:

- what to search for;
- how to distinguish a real engineering project from a tutorial;
- which repository fits their technical foundation, available time, and target role;
- what the upstream project already provides and what they can still contribute;
- whether the project can withstand detailed resume and interview questions.

HunterProject does not rank repositories by stars alone. It evaluates repository quality, role fit, user fit, and career value separately. Important conclusions should be supported by dependencies, configuration, entry points, tests, CI, or key implementation code whenever possible.

## Current status

This is an early **instruction-first Agent Skill** for workflow testing. It currently focuses on project discovery and selection and does not yet include a deterministic GitHub API search script or a complete role-template library.

The Skill covers:

- understanding the user and target role;
- building a search profile;
- searching, filtering, and verifying candidate repositories;
- returning 3–5 qualified candidates without padding the list when fewer qualify;
- deeply inspecting the 1–2 projects selected by the user;
- recommending a primary project, a backup, and directions for personal extension.

Implementation, deployment, resume writing, and interview preparation belong to downstream workflows and are not completed by this Skill.

## Real example

[`China AI application / Agent internship: a two-month RAG project search`](examples/ai-agent-rag-internship.md) records one complete run. Starting from the user's background and the role knowledge map, it recalled roughly 50 results, statically inspected 8 repositories, compared 4 candidates, and deeply inspected the 2 selected by the user before producing a primary project, a backup, and an eight-week extension plan.

The example distinguishes **Verified / Claimed / Inferred / Unknown** evidence. It is a static-inspection snapshot dated 2026-08-16; no third-party code was executed, and README claims were not treated as verified facts.

## Validation status

- 1 end-to-end real scenario completed;
- 12 behavior cases specified;
- the full automated suite has not been run, so no overall pass rate is claimed.

## Skill location

The portable Skill is located at:

```text
skills/hunt-github-projects/
```

The core `SKILL.md` uses only the standard `name`, `description`, and Markdown instructions. `agents/openai.yaml` contains optional OpenAI interface metadata; the core workflow does not depend on it.

## Install

Clone the repository:

```bash
git clone https://github.com/yu-yaofeng/HunterProject.git
```

Then copy or link the complete `skills/hunt-github-projects` folder into a Skills directory supported by your agent.

Example Codex user-level location:

```text
$HOME/.agents/skills/hunt-github-projects/
```

Example Codex project-level location:

```text
<project>/.agents/skills/hunt-github-projects/
```

Other agents may use different discovery directories. Consult the current documentation for the target platform. Keep the complete Skill folder together instead of copying only `SKILL.md`.

## Usage examples

When almost no background information is available:

```text
$hunt-github-projects I have no projects yet. Help me find a GitHub project for my job search.
```

When the technical stack and available time are already known:

```text
$hunt-github-projects I know Java, Spring Boot, and MySQL, want a backend internship,
and have six weeks. Find several projects worth extending that are not mall clones.
```

When a JD and complete background are already available:

```text
$hunt-github-projects Here is my JD and personal background.
Skip information I have already provided and find 3–5 candidates supported by code evidence.
```

## Evaluation

Behavior cases are available in [`evaluations/cases.md`](evaluations/cases.md). The v0.1 evaluation focuses on:

- learning about the user progressively;
- using the fast lane when enough information is already available;
- degrading honestly when live access is unavailable;
- refusing to pad the shortlist when too few candidates qualify;
- evaluating repository quality separately from user fit;
- invalidating stale rankings when the user changes constraints;
- asking the user to choose candidates before producing final primary and backup recommendations;
- maintaining the boundary between project discovery and downstream implementation.

## License

HunterProject is released under the [MIT License](LICENSE).

## Independence

HunterProject is an independent community project. It is not affiliated with or endorsed by GitHub, OpenAI, or the maintainers of repositories it may discover and evaluate. Product names and trademarks belong to their respective owners.
