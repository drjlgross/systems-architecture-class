# Systems Architecture: Learning Benchmarks & Self-Assessment

**Purpose:** A testable framework for evaluating meaningful progress through the systems architecture syllabus. Self-assessed, but structured enough to give clear yes/no answers rather than vague impressions.

---

## Core Hypothesis

> After completing this syllabus, I can accurately name the design principles at work in a system I've never seen before, identify where it violates them, and propose a specific structural improvement — using the correct vocabulary — without assistance.

Everything else is a sub-test of this.

---

## Benchmark Tests

### Vocabulary
- [ ] Given any script or codebase, can I identify and correctly name at least three design principles it embodies or violates? (Not "this seems messy" — "this has high coupling between modules X and Y because...")
- [ ] Can I explain the difference between an interface and an implementation to someone non-technical without using either word?

### Design reading
- [ ] Given a system I didn't build, can I draw its architecture in a reasonable Mermaid diagram — components, dependencies, data flow — in under 20 minutes?
- [ ] Can I look at that diagram and name its architectural style (pipe-and-filter, layered, event-driven, etc.)?

### Design critique
- [ ] Can I read someone else's code and produce a written critique that names at least two code smells by their actual names, explains why each is a problem, and proposes a specific refactor?
- [ ] Can I evaluate a proposed API design and identify at least one place where it violates a named principle (minimal surface area, fail-fast, consistency, etc.)?

### Structural assessment (the new one)
- [ ] Given a script I didn't write, can I produce a written structural assessment in under 15 minutes that identifies problems at the design level — not just the functional level?

### Self-description
- [ ] Can I answer "walk me through how you'd design X from scratch" in a conversation or client context with a coherent, structured answer that references tradeoffs between at least two architectural approaches?
- [ ] Can I write three resume bullets describing my Era pipeline work using this vocabulary that would be legible to a senior software engineer reading them?

---

## The Bright Line Test

Take any one Era pipeline script. 

**Before:** I can explain what it does.

**After:** I can explain what it *is* — its specification, its abstraction boundary, the design pattern it uses or should use, the smell it currently has, and what I'd change and why.

**Pass criteria:** Ten-minute verbal (or written) walkthrough of `pull_doc` without notes, covering all five dimensions above.

---

## Two Modes of Code Evaluation

A useful frame for tracking the shift this course is meant to produce:

**Mode 1 — Behavioral (current default):** Does it do what I expect when I run it? Tests outputs. Catches surface failures. Runs after execution.

**Mode 2 — Structural (the target):** Is this well-formed? Tests design. Catches problems that work today but break under change, composition, or maintenance. Runs before execution.

Progress means Mode 2 becoming available and increasingly automatic alongside Mode 1 — not replacing it.

---

## What This Course Won't Give Me

Boundary condition for the hypothesis — scope-setting, not a gap:

- I won't be able to build a production-grade system from scratch using formal methods.
- I will be able to reason about and communicate system design clearly.
- I will be able to direct AI-assisted development with precision rather than relying on default interpretations.
- I will be able to evaluate code structure, not just functional behavior.

---

## Notes on Self-Assessment

- This is not a formal degree program. Done is self-assessed.
- The benchmark tests above are designed to be yes/no wherever possible.
- The reflection prompts in the syllabus are the primary practice mechanism — skipping them means the vocabulary stays abstract rather than landing against real work.
- Units 3 and 4 (Specifications and Abstract Data Types) are the predicted stall points. The concepts click suddenly, usually mid-reflection. Don't mark them done until the reflection prompt feels genuinely answered.
- Revisit this document at the halfway point (after Unit 6 or 7) and at completion.
