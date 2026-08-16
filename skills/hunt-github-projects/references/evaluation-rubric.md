# Candidate Evaluation Rubric

## Contents

- Hard exclusions
- Risk flags
- Four independent scores
- Evidence confidence
- Candidate roles
- Qualification and no-padding rule

## Hard exclusions

Exclude a candidate from Base recommendations when any of these is true and cannot be resolved:

- the repository is fabricated, inaccessible, empty, or only a link collection;
- it contains no meaningful implementation beyond generated scaffolding;
- it is a tutorial whose completed form leaves no credible ownership space;
- the core technology or feature is contradicted by inspected code;
- the scope is clearly impossible within the user's time or resources;
- the project creates an unacceptable legal, safety, or licensing risk;
- it is a duplicate fork or near-identical copy of a stronger candidate;
- it cannot plausibly demonstrate the target role.

A repository excluded as a Base may still qualify as a Reference or Component if that use is honest and useful.

## Risk flags

Do not automatically exclude without context, but flag:

- archived or low-activity status;
- missing or restrictive license;
- weak documentation or setup instructions;
- no tests or CI;
- hard-coded secrets or insecure defaults;
- expensive external services or hardware;
- very large monorepo or steep prerequisite stack;
- mature product with little meaningful extension space;
- common bootcamp, tutorial, or clone-project pattern;
- heavy dependence on one vendor or obsolete framework.

## Four independent scores

Score each dimension from 0 to 5. Show the dimensions separately; a total score is optional and must not hide a failing dimension.

### Repository quality

| Score | Meaning |
|---|---|
| 0 | unusable or deceptive |
| 1 | severe structural or maintenance problems |
| 2 | usable only with substantial uncertainty |
| 3 | credible foundation with manageable weaknesses |
| 4 | strong engineering evidence and maintainability |
| 5 | exceptional engineering quality for its intended scope |

Consider code organization, documentation, tests, maintenance, setup, security posture, and license.

### Role fit

Measure coverage of must-have role signals, coherence with the JD, and technical depth relevant to the target subrole. Do not reward unrelated complexity.

### User fit

Measure learning distance, time, resources, operating system, budget, and likelihood that the user can explain and extend the project independently.

### Career value

Measure ownership space, differentiation, demonstrability, technical discussion depth, and whether a meaningful extension would create a credible hiring signal.

Penalize clone saturation and projects that are impressive only because the upstream maintainers already built everything.

## Evidence confidence

Report confidence separately:

- **High:** core recommendation claims are Verified.
- **Medium:** most core claims are Verified; some important constraints are Claimed or Inferred.
- **Low:** important claims remain Unknown or only Claimed.

Do not present Low-confidence candidates as the sole final recommendation without clearly stating the limitation.

## Candidate roles

- **Base:** user can reasonably fork or reimplement a foundation and make substantial owned changes.
- **Reference:** useful design or implementation source, but unsuitable as the main owned project.
- **Component:** a focused module or library that can support a broader project.

Do not label a repository Base solely because it is easy to clone.

## Qualification and no-padding rule

A Base candidate normally needs:

- no unresolved hard exclusion;
- Role fit at least 3;
- User fit at least 3;
- Career value at least 3;
- sufficient evidence to explain material uncertainty.

Repository quality below 3 requires a specific, manageable recovery argument. Otherwise classify it as Reference/Component or exclude it.

Return 3-5 qualified candidates only when 3-5 exist. If fewer qualify, return fewer. If none qualify, produce a no-result report and propose relaxing one constraint at a time.
