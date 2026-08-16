# HunterProject

HunterProject helps programmers discover, verify, and compare open-source projects worth building on for a job search.

> 中文定位：先了解这个人想成为什么样的程序员，再为他从 GitHub 找到适合求职、能够继续改造的开源项目。

## Why it exists

Many developers know that GitHub contains valuable projects but do not know what to search for, how to distinguish a real engineering project from a tutorial, or which repository fits their own skills, timeframe, and target job.

HunterProject changes the interaction from "keyword in, repository out" to:

```text
person
→ target role or JD
→ job knowledge map
→ search profile
→ live GitHub discovery
→ code-evidence verification
→ 3-5 qualified candidates
→ user selects 1-2
→ primary and backup recommendation
```

## Current status

This repository contains an early, instruction-first Agent Skill for workflow testing. It does not yet include a deterministic GitHub API search script or complete role-pack library.

The Skill focuses on discovery and selection. It deliberately stops before project implementation, resume writing, and interview preparation.

## Skill location

The portable Skill is located at:

```text
skills/hunt-github-projects/
```

Its core `SKILL.md` uses only `name`, `description`, and Markdown instructions. `agents/openai.yaml` is optional OpenAI-specific UI metadata; the core workflow does not depend on it.

## Try it

Invoke the Skill with requests such as:

```text
I have no projects yet. Help me figure out what kind of GitHub project fits my job search.
```

```text
I know Java and Spring Boot, want a backend internship, and can spend six weeks. Help me find several projects worth extending.
```

```text
Here is my JD and background. Skip questions I already answered and find 3-5 qualified GitHub candidates.
```

For Codex, the current official documentation describes repository skills under `.agents/skills/<skill-name>` and user skills under `$HOME/.agents/skills/<skill-name>`. Copy or link the complete `hunt-github-projects` directory into the appropriate skills directory, then invoke `$hunt-github-projects`.

Official OpenAI documentation: <https://learn.chatgpt.com/docs/build-skills>

Other agents may use different discovery directories. Keep the complete Skill folder together and consult that agent's current documentation.

## Evaluate it

Use the behavior cases in `evaluations/cases.md`. The first release should pass the guided-intake, fast-lane, no-web, no-padding, user-feedback, and evidence-labeling cases before adding automation.

## License

HunterProject is released under the [MIT License](LICENSE).

## Independence

HunterProject is an independent community project. It is not affiliated with or endorsed by GitHub, OpenAI, or the maintainers of repositories it may discover and evaluate. Product names and trademarks belong to their respective owners.
