# Intake and Search Profile

## Contents

- Routing before questions
- Required and conditional fields
- Behavior-based calibration
- Question rules
- Search profile format
- Updating and saving profiles

## Routing before questions

Before asking anything, extract facts from the current message, conversation, attached JD, resume, and any pasted profile.

Use this decision logic:

```text
known = extract all usable fields
missing = required fields not established

if target role is absent or materially ambiguous:
    if personal foundation is also absent:
        ask about current technical foundation first
    else:
        help choose or narrow the target role
elif a required field is missing:
    ask only for the highest-impact missing field
elif two interpretations would materially change search results:
    ask one clarification
else:
    print a compact search profile and begin search
```

The stages are a default route, not a mandatory questionnaire. Skip any stage whose information is already available.

## Required and conditional fields

### Required before live project search

| Field | What is sufficient |
|---|---|
| Current foundation | Main languages/frameworks plus evidence of what the user can do independently |
| Target | A sufficiently narrow target role or a concrete JD |
| Time | Weekly availability, delivery window, or another useful scope constraint |

### Conditionally required

| Field | Ask only when |
|---|---|
| Hiring market or location | No concrete JD exists and local hiring expectations affect the knowledge map |
| Compute or hardware | AI, data, embedded, mobile, graphics, or other resource-sensitive work is involved |
| Budget | Paid APIs, cloud services, datasets, or hardware could be required |
| Target level | Internship, new-grad, junior, or experienced scope is unclear |
| Preferred business domain | Several equally valid domains would produce very different candidates |

### Optional unless consequential

- degree and major;
- graduation date;
- company size preference;
- full resume;
- unrelated work history;
- visual style preference.

Do not block search on optional information.

## Behavior-based calibration

Prefer evidence such as:

- built and debugged an API independently;
- designed a relational schema;
- written automated tests;
- deployed an application;
- implemented authentication;
- diagnosed production-like failures;
- trained or evaluated a model;
- built a CI/CD pipeline;
- integrated a device or external service.

Ask only role-relevant calibration questions. Treat "watched a course", "used in a tutorial", and "built independently" as different evidence levels.

## Question rules

- Ask one topic or at most two tightly coupled questions per turn.
- Explain briefly why a sensitive or unusual question affects project selection.
- Do not repeat facts the user already supplied.
- Do not ask for exact personal identifiers.
- Prefer choices only when the user is genuinely uncertain; do not force a fixed menu onto a specific answer.
- If the user says "start searching" and the minimum profile is complete, start.

Default first question when almost nothing is known:

> Before choosing a role or repository, what technologies can you currently use in practice, and what have you built independently with them?

Default role question after foundation is known:

> Which role do you want to investigate deeply for your job search? If the direction is still broad, describe the kind of work you want to do and I will help narrow it.

## Search profile format

Use this format internally and show a compact version to the user:

```yaml
profile_version: 1
target:
  role_family: ""
  subrole: ""
  level: ""
  market: ""
  jd_provided: false
user:
  current_stack: []
  demonstrated_capabilities: []
  learning_only: []
constraints:
  delivery_window: ""
  weekly_time: ""
  compute: ""
  budget: ""
  excluded_stacks: []
project_signal:
  must_cover: []
  nice_to_have: []
  preferred_domains: []
  differentiation_goal: ""
assumptions: []
unknowns: []
```

Do not invent empty fields. Use `unknown` or omit an optional field.

## Updating and saving profiles

If the user changes a field, identify which downstream conclusions are stale:

- role or JD change invalidates the knowledge map, queries, and rankings;
- time or resource change invalidates user-fit and feasibility scores;
- business-domain change invalidates domain-specific queries and career-value scores;
- stack preference change invalidates compatibility and learning-cost estimates.

Offer to save a Markdown profile only with consent. Avoid persisting resumes, names, contact details, or other unnecessary personal data. When saving is impossible, print a copyable profile.
