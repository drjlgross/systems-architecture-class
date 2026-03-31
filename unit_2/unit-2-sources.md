## Parnas Paper 

- [[criteria_for_modularization.pdf|Here]].
## MIT Readings

- **Reading 6: Specifications** — `https://ocw.mit.edu/ans7870/6/6.005/s16/classes/06-specifications/` — introduces the idea that a module exposes _what_ it does, not _how_. Direct setup for information hiding.
- **Reading 9: Avoiding Debugging** — `https://ocw.mit.edu/ans7870/6/6.005/s16/classes/09-avoiding-debugging/` — makes the _payoff_ case for modularity: why isolated modules make bugs easier to localize and fix.
- **Reading 14: Interfaces** — `https://ocw.mit.edu/ans7870/6/6.005/s16/classes/14-interfaces/` — the Java-specific treatment of interface vs. implementation, which is the formal version of information hiding.

## Previous Unit Context 

- Truncated syllabus (see below, overall course goal and the unit 2 text specifically)
- Previous podcast transcript, [[unit-1-podcast-transcript|here]].

---

## Syllabus: Overall

Systems Architecture: Self-Study Syllabus

Purpose: A sequenced curriculum for building conceptual fluency in software systems design. Draws on MIT 6.031 (Software Construction) and the University of Alberta Software Design & Architecture specialization (Coursera). Adapted for self-directed learning alongside real pipeline work.

How to use this:
- Each unit has a core question — the thing you should be able to answer fluently by the end.
- Units build on each other; don't skip forward.
- For each unit, there is a canonical reading/reference and a reflection prompt to apply the concept to real work.

---

## Unit 2: Modularity and Decomposition

**Core question:** How do you break a system into parts that can be understood and changed independently?

**Concepts:**
- What modularity means: the ability to change one part without touching others
- Decomposition strategies: by function, by data, by abstraction level
- MECE (mutually exclusive, collectively exhaustive) as a decomposition principle
- Single responsibility: each module does one thing
- Information hiding: modules expose *what* they do, not *how*
- Coupling vs. cohesion — the two axes of module quality

**Canonical reference:** Parnas, "On the Criteria to be Used in Decomposing Systems into Modules" (1972) — short, foundational, free online

**Reflection prompt:** Draw the dependency graph of your pipeline scripts. Which ones are tightly coupled? Which are cleanly isolated? Where would a change ripple?

--- 
### NotebookLM Link:

https://notebooklm.google.com/notebook/15d8849c-f426-4aa9-849b-045bb13a15e1

---

### Podcast Prompt: 

"Generate a podcast episode hosted by Vera and Chris explaining modularity and decomposition in software design, aimed at a self-taught developer who has already shipped a real multi-script pipeline that talks to Google Docs and Google Drive. The listener understands what a function is, knows what an API is, and has just completed a unit on what makes software good — they're familiar with the 'big three' properties and the fail-fast principle.

Focus on the core question: how do you break a system into parts that can be understood and changed independently? Cover what modularity actually means (the ability to change one part without touching others), the difference between decomposing by function versus by information hiding (use Parnas as the anchor here — this is the key conceptual shift), single responsibility, and the coupling vs. cohesion tradeoff as the two axes of module quality.

Use concrete examples where possible — a multi-script pipeline that shares a manifest file is fair game. Explain why information hiding is a design goal rather than just an organizational preference, and make the Parnas insight feel like a genuine revelation: that the natural-seeming way to decompose a system (by the steps it performs) is often the wrong way."

---

### Podcast Transcript: 

Link, [[unit-2-podcast-transcript|here]].

---

### Reflection 

Doc, [[unit-2-reflection|here]].
