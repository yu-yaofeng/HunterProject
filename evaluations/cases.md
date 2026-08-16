# HunterProject v0.1 behavior cases

Use these as forward-test prompts. Evaluate behavior and evidence discipline, not whether a particular repository happens to rank first.

## Case 1: Almost no information

Prompt:

> I have no projects. Find me something good on GitHub for getting a job.

Expected:

- Ask about current practical technical foundation first.
- Do not ask for all profile fields at once.
- Do not start repository search yet.

## Case 2: Foundation known, role missing

Prompt:

> I can independently build a React frontend and call REST APIs. I have eight weeks but do not know which frontend role to focus on.

Expected:

- Do not repeat stack or time questions.
- Help narrow the frontend subrole or desired work.
- Ask at most one topic in the response.

## Case 3: Fast lane

Prompt:

> I am applying for Java backend internships in China. I can build Spring Boot REST APIs with MySQL, have only tutorial-level Redis experience, and can spend six weeks. I want a non-mall project that demonstrates auth, caching, testing, Docker, and one meaningful distributed-systems concept. Find several GitHub bases.

Expected:

- Summarize the complete profile.
- Start search without repeating intake or requesting confirmation.
- Use current evidence and return 3-5 candidates only if they qualify.

## Case 4: Full JD and resume-like context

Prompt:

> Here is the JD and my background. [Provide a detailed JD and skills.] I want RAG-related work and have six weeks.

Expected:

- Extract known information before asking questions.
- Ask only about a missing field that would materially change search.
- Distinguish required, preferred, and boilerplate JD language.

## Case 5: Broad role ambiguity

Prompt:

> I want an AI project.

Expected:

- Learn the user's foundation if unknown.
- Distinguish AI application/Agent, ML engineering, data science, and research-like paths when relevant.
- Do not search against the broad word "AI" alone.

## Case 6: No live access

Prompt:

> Find current GitHub projects, but the agent has no web or GitHub access.

Expected:

- State that live discovery cannot be verified.
- Offer search queries or request repository URLs.
- Do not invent repositories, activity, stars, licenses, or code evidence.

## Case 7: Too few qualified candidates

Setup:

- Only one candidate passes hard filters.

Expected:

- Return one candidate, not three padded choices.
- Explain rejected candidates or binding constraints.
- Offer to relax one constraint at a time.

## Case 8: Same repository, different users

Setup:

- Candidate repository requires Kubernetes, Kafka, and several services.
- User A has ten weeks and platform-engineering experience.
- User B is a backend beginner with three weeks.

Expected:

- Repository quality may remain the same.
- User fit and final ranking must differ materially.

## Case 9: Overexposed project

Setup:

- A high-star, well-engineered repository is a common bootcamp clone with little ownership space.
- A smaller repository strongly matches the JD and has clear extension seams.

Expected:

- Do not let stars decide the ranking.
- Explain clone saturation and ownership tradeoffs.

## Case 10: User changes direction

Prompt sequence:

1. Build a profile for a Java backend project.
2. User changes the delivery window from eight weeks to three and rejects paid cloud services.

Expected:

- Update the profile.
- Invalidate feasibility and cost-dependent rankings.
- Do not continue presenting stale recommendations.

## Case 11: Candidate count and feedback loop

Setup:

- Five qualified candidates exist.

Expected:

- Present 3-5 candidates with distinct tradeoffs and comparable detail.
- Ask the user to select one or two for deep inspection.
- Finalize a primary and backup only after that inspection.

## Case 12: Scope boundary

Prompt:

> Now implement the selected project and write my resume bullets.

Expected:

- State that discovery is complete.
- Hand off implementation and resume work to an appropriate downstream workflow.
- Do not silently expand the HunterProject Skill into an end-to-end job coach.
