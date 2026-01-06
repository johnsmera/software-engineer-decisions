# Stabilizing a React Project Under Deadline Pressure

This repository documents a real-world intervention in a React codebase that was close to release and showing clear signs of structural risk.

This is not a tutorial, a framework, or a checklist.
It is a technical case about decision-making under time pressure, team dynamics, and trade-offs between code quality and business continuity.

---

## Context

The project was an internal system developed during the pandemic investment bubble.
The company hired multiple developers in a short time frame to build a React-based application under a fixed deadline.

I joined the project late in the cycle, when the system was already close to release.

From the first technical review, it was clear that the main risk was not missing the deadline — it was shipping a system that would become unstable and unmaintainable immediately after launch.

---

## Initial State

The codebase presented multiple compounding issues:

- No TypeScript (acceptable given the context, but relevant)
- No ESLint or static analysis
- Inconsistent coding patterns across files
- Extensive prop drilling and implicit dependencies
- Side effects declared after render logic
- Debug artifacts (`console.log`) spread across production code
- No automated tests
- Weak architectural boundaries, loosely resembling MVC

None of these issues alone would justify a rewrite.
Together, they represented a high probability of post-launch failure.

---

## Constraints

- The deadline could not be moved
- A full rewrite was not an option
- The team was already emotionally invested in the existing code
- Changes needed to reduce risk, not create new ones

The goal was not to "improve code quality" in the abstract.
The goal was to reduce the probability of system collapse after release.

---

## Key Decisions

### 1. Introduce ESLint as a Diagnostic Tool

Instead of arguing subjectively about code quality, ESLint was introduced to make structural issues visible.

The initial lint run surfaced a large number of violations, which helped shift the discussion from opinion to evidence.

Each rule was reviewed with the team:
- Why it existed
- What risk it mitigated
- Whether it made sense in this context

Rules that added friction without clear value were not enforced.

---

### 2. Standardize Patterns Before Adding Features

Before any new functionality, the team aligned on:
- Component structure
- Hook usage conventions
- Naming patterns
- File organization

This reduced cognitive load and made future changes predictable.

---

### 3. Establish Git Discipline

Basic but essential practices were introduced:
- Clear branching strategy
- Meaningful commit messages
- Pull requests with technical intent, not just delivery pressure

This was less about process and more about creating a shared mental model of the system.

---

### 4. Avoid Premature Abstractions

Given the time constraints, abstractions were introduced only when they removed duplication *and* reduced risk.

Complex architectural refactors were explicitly avoided.

---

## Outcome

- The system was delivered on time
- No major incidents occurred post-launch
- The codebase remained stable under ongoing feature development
- The team adopted the established practices and continues to use them

Since then, multiple other systems were built following similar principles, all of them currently in production without structural degradation.

---

## Why This Case Matters

Most engineering failures do not come from lack of knowledge.
They come from:
- Poor timing of technical decisions
- Ignoring team dynamics
- Treating "best practices" as dogma instead of tools

This case demonstrates how small, well-scoped interventions can significantly reduce long-term risk without derailing delivery.

---

## Scope and Limitations

This repository does not include proprietary source code.
It focuses on decisions, trade-offs, and reasoning — not implementation details.

The intent is to share how to think about stabilizing systems, not to prescribe a universal solution.

---

## About

This case reflects my approach to software engineering:
building systems that scale in complexity without becoming ungovernable.

