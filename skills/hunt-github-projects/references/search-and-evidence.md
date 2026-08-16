# Search and Evidence Workflow

## Contents

- Capability gate
- Query families
- Candidate recall
- Repository inspection
- Evidence levels
- Freshness, limits, and safety

## Capability gate

Before claiming live results, establish whether the environment can:

- search the current web or GitHub;
- open repository pages;
- inspect file trees and source files;
- observe maintenance, release, issue, and license information.

Use the tools available in the current agent. Do not name a platform-specific tool in user-facing instructions unless needed. If live access is unavailable, generate queries or inspect user-provided URLs instead.

## Query families

Generate multiple families from the search profile and role map:

1. **Stack + business domain**  
   Example: `spring boot booking platform redis`
2. **Mechanism + architecture**  
   Example: `event driven order service outbox kafka`
3. **Role signal + production feature**  
   Example: `fastapi rag evaluation tracing`
4. **Extension opportunity**  
   Example: `starter platform plugin architecture open issues`
5. **Code evidence**  
   Search dependencies, configuration names, APIs, classes, or functions that indicate real implementation.
6. **Adjacent terminology**  
   Expand synonyms, ecosystem terms, and business-language equivalents.

Use several narrow queries instead of one broad query. Search in the ecosystem's dominant language as well as the user's language when useful.

## Candidate recall

- Build a broad internal pool before ranking.
- Avoid aggressive star thresholds during recall.
- Record the query or path that found each candidate.
- Diversify by business domain, architecture, maturity, and project size.
- Include lower-star repositories when their code and role fit are stronger.
- Avoid returning multiple forks or near-identical templates as separate choices.

Collect when available:

- URL, description, primary language, topics;
- last meaningful activity and release cadence;
- contributors, issues, and project status;
- license;
- setup path and external dependencies;
- tests, CI, container or deployment artifacts;
- architecture and feature evidence;
- likely Base, Reference, or Component role.

## Repository inspection

Prefer static inspection in this order:

1. repository status, license, activity, and releases;
2. dependency manifests and lockfiles;
3. top-level structure and entry points;
4. configuration and data model;
5. core request, data, model, task, or device flows;
6. tests, CI, deployment, logging, and error handling;
7. extension seams such as plugins, interfaces, open roadmap items, or isolated modules.

Do not clone or execute a repository merely to improve a first shortlist. If later execution is needed, use a safe downstream workflow and disclose the additional risk.

## Evidence levels

Use exactly these labels:

- **Verified:** confirmed in current repository metadata or specific code/config/test evidence.
- **Claimed:** stated by README or project documentation but not confirmed in implementation.
- **Inferred:** reasonably inferred from structure or dependencies but still uncertain.
- **Unknown:** unavailable, inaccessible, or not checked.

For important claims, cite a repository URL and, when possible, a file path or precise artifact. Do not upgrade Claimed or Inferred evidence to Verified without inspection.

## Freshness, limits, and safety

- Include the inspection date in final results.
- Distinguish repository age from abandonment; stable projects can have infrequent commits.
- Note API limits, inaccessible files, missing branches, or incomplete inspection.
- Never fabricate current stars, releases, licenses, or commit activity.
- Treat missing license as a risk, not automatically as permission.
- Never expose discovered secrets or credentials.
- Avoid running untrusted install scripts during discovery.
- If current access is blocked, state which conclusions remain Unknown.
