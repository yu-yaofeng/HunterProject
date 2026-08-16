# Output Contract

## Contents

- Search profile
- Initial shortlist
- Candidate card
- Feedback checkpoint
- Deep comparison and final recommendation
- No-result report
- Ownership and persistence

## Search profile

Before live search, show a compact profile:

```markdown
### Search profile

- Target role:
- Current foundation:
- Must cover:
- Nice to have:
- Constraints:
- Avoid:
- Time window:
- Differentiation goal:
- Assumptions:
```

Do not stop for confirmation when the profile is unambiguous and the user has already asked to search. Continue in the same turn.

## Initial shortlist

Default to 3-5 qualified candidates with distinct tradeoffs:

| Candidate | Role | Best reason | Main tradeoff | Role fit | User fit | Career value | Confidence |
|---|---|---|---|---:|---:|---:|---|
| Repository A | Base | ... | ... | 0-5 | 0-5 | 0-5 | High/Medium/Low |

Then state:

- recommended Base;
- alternative Bases;
- optional Reference or Component;
- how many candidates were examined internally when known;
- inspection date and access limitations.

Never hide that fewer than three qualified candidates were found.

## Candidate card

For every presented candidate include:

```markdown
### owner/repository — Base | Reference | Component

- URL:
- Why it matches this user and role:
- Verified knowledge signals:
- Claimed, inferred, or unknown signals:
- Repository health:
- Ownership and extension space:
- Differentiation or clone-saturation risk:
- Main risks:
- What the user would need to build:
```

Use comparable depth for every candidate. Do not give the favorite rich detail and reduce alternatives to bare links.

## Feedback checkpoint

After the first shortlist, ask the user to choose one or two candidates for deeper inspection. Also allow feedback such as:

- prefer a different business domain;
- reduce or increase difficulty;
- avoid a framework, vendor, cost, or hardware dependency;
- prioritize demo impact, architecture depth, or JD alignment.

Update the profile and rerun affected search steps when feedback changes the decision.

## Deep comparison and final recommendation

For the selected one or two candidates, compare:

- architecture and core flows;
- role knowledge coverage;
- setup and resource requirements;
- extension seams;
- expected personal contribution;
- maintenance, license, security, and dependency risk;
- demonstration and technical-discussion potential.

Conclude with:

```markdown
### Final recommendation

- Primary project:
- Backup project:
- Why the primary wins for this person:
- Minimum owned changes needed before job use:
- Failure conditions that should trigger switching to the backup:
- Suggested downstream next step:
```

Do not call a project resume-ready or interview-ready merely because it was selected.

## No-result report

If no candidate qualifies, provide:

- search coverage attempted;
- binding constraints;
- representative rejected candidates and rejection reasons;
- one proposed constraint relaxation;
- a request for agreement before searching again.

Do not recommend a weak repository to avoid an empty answer.

## Ownership and persistence

Always separate:

- upstream project capabilities;
- proposed user modifications;
- work that would need to be verified after implementation.

Respect licenses and attribution. Never advise presenting upstream work as personal authorship.

Offer a reusable Markdown profile at the end. Save it only with user consent and omit unnecessary personal identifiers.
