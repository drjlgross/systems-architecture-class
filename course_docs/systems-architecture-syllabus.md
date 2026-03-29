# Systems Architecture: Self-Study Syllabus

**Purpose:** A sequenced curriculum for building conceptual fluency in software systems design. Draws on MIT 6.031 (Software Construction) and the University of Alberta Software Design & Architecture specialization (Coursera). Adapted for self-directed learning alongside real pipeline work.

**How to use this:**
- Each unit has a *core question* — the thing you should be able to answer fluently by the end.
- Units build on each other; don't skip forward.
- For each unit, there is a canonical reading/reference and a reflection prompt to apply the concept to real work.

---

## Unit 1: What Makes Software Good

**Core question:** What are the properties we're actually trying to achieve, and why do they trade off against each other?

**Concepts:**
- The "big three": safe from bugs, easy to understand, ready for change (MIT 6.031 framing)
- Why "correctness" alone is insufficient
- The tension between optimizing for present correctness vs. future flexibility
- Why readability is a design goal, not a stylistic preference

**Canonical reference:** MIT 6.031 Reading 1 (available free at web.mit.edu/6.031)

**Reflection prompt:** Look at one script in your Era pipeline. Which of the three properties does it do well? Which would be hardest to maintain as requirements change?

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

## Unit 3: Specifications and Invariants

**Core question:** How do you define what a piece of code is *supposed* to do, separately from how it does it?

**Concepts:**
- What a specification is: a contract between a module and its callers
- Preconditions: what must be true before a function is called
- Postconditions: what will be true after it returns
- Invariants: properties that must always hold (class invariants, loop invariants)
- The difference between a spec and an implementation
- Why specs matter even informally — they define the interface others can rely on
- Defensive programming vs. design-by-contract

**Canonical reference:** MIT 6.031 Readings 6–7 (Specifications, Designing Specifications)

**Reflection prompt:** Pick one function in your pipeline. Write its preconditions and postconditions informally in plain English. Does the code actually enforce them? What happens if a caller violates them?

---

## Unit 4: Abstract Data Types

**Core question:** How do you design data structures so that callers depend on *what they do*, not *how they're built*?

**Concepts:**
- Abstract data type (ADT): a data type defined by its operations, not its representation
- Representation independence: callers cannot and should not know the internal structure
- The difference between an interface and an implementation
- Abstraction functions and representation invariants
- Mutability vs. immutability — and why immutability is the safer default
- How ADTs enable modularity: you can change the internals without breaking callers

**Canonical reference:** MIT 6.031 Readings 10–11 (Abstract Data Types, Abstraction Functions & Rep Invariants)

**Reflection prompt:** Your pipeline's manifest is a data structure. What operations does it expose? What would break if you changed its internal format (e.g., from a JSON dict to a SQLite table)? This gap is the representation leaking through.

---

## Unit 5: Testing

**Core question:** What is testing actually for, and how do you design tests that give you real confidence?

**Concepts:**
- Testing as specification verification, not bug hunting
- Test-first design (TDD): why writing tests before code clarifies specs
- Black-box vs. glass-box testing
- Coverage: line, branch, path — and why 100% coverage is not the goal
- Partitioning input space: testing boundaries and edge cases systematically
- Unit tests vs. integration tests vs. end-to-end tests — when each is appropriate
- The relationship between a good spec and a testable function

**Canonical reference:** MIT 6.031 Reading 3 (Testing)

**Reflection prompt:** Which of your pipeline scripts has no tests? What would a unit test for `doc_converter` actually check? Write the test spec in plain English (not code).

---

## Unit 6: Version Control Philosophy

**Core question:** What does version control actually represent, and why do branching models exist?

**Concepts:**
- What a commit represents: a named, reproducible state of a system
- The DAG (directed acyclic graph) model of history — why history is a tree, not a line
- Branching: what a branch is conceptually, not mechanically
- Branching strategies: trunk-based vs. feature branches vs. gitflow — and the tradeoffs
- The purpose of a commit message: communicating *intent*, not just *change*
- What a merge is, and why conflicts happen
- Tags, releases, and reproducibility

**Canonical reference:** MIT 6.031 Reading 5 (Version Control). For deeper philosophy: "A successful Git branching model" (nvie.com/gitflow — free)

**Reflection prompt:** Look at your Era pipeline commit history. Do your messages communicate intent or just describe changes? What would a new contributor need to understand from the history alone?

---

## Unit 7: APIs — Design and Construction

**Core question:** What makes an API well-designed, and what principles govern the boundary between a module and its callers?

**Concepts:**
- What an API is: a formal interface between components that may evolve independently
- API design principles:
  - Minimal surface area: expose only what callers need
  - Consistency: similar things should work similarly
  - Fail-fast: surface errors at the boundary, not silently downstream
  - Irreversibility: APIs are hard to change once callers depend on them
- Synchronous vs. asynchronous APIs
- REST as an architectural style for HTTP APIs: resources, verbs, statelessness
- Authentication patterns: API keys, OAuth, token-based auth
- Versioning: why it's hard and how to think about it

**Canonical reference:** University of Alberta Software Architecture course (Coursera) — "Service-Oriented Architecture" module. For REST: Fielding's dissertation Chapter 5 intro (free online).

**Reflection prompt:** Your pipeline uses both the Google Drive API and the Google Docs API. Where does each API's design make your code easier or harder? What would you design differently if you were building the API yourself?

---

## Unit 8: Design Patterns

**Core question:** What recurring structural problems in software design have known, named solutions?

**Concepts:**
- What a design pattern is: a reusable solution to a recurring design problem
- Why patterns matter: shared vocabulary, not templates to copy
- **Creational patterns** — how objects/modules are created:
  - Factory: decouple creation from use
  - Singleton: ensure one instance (and why it's often a code smell)
- **Structural patterns** — how components are composed:
  - Adapter: translate between incompatible interfaces
  - Decorator: add behavior without changing the original
  - Facade: simplify a complex subsystem behind a clean interface
- **Behavioral patterns** — how components communicate:
  - Observer: notify dependents when state changes (the pub/sub pattern)
  - Strategy: swap algorithms behind a consistent interface
  - Command: encapsulate a request as an object
- Anti-patterns: patterns that *look* like solutions but create problems (God Object, Spaghetti Code, Shotgun Surgery)

**Canonical reference:** University of Alberta "Design Patterns" course (Coursera). For the canonical source: *Design Patterns* (Gang of Four) — you don't need to read it all; the intro + any 3 patterns you recognize in your work.

**Reflection prompt:** Your `stage`, `pull_doc`, and `pull_comments` scripts all touch the manifest. Is that a God Object problem? What pattern might give each script a cleaner, more isolated relationship to shared state?

---

## Unit 9: UML — Visual Notation for Software Design

**Core question:** What is the standard visual language engineers use to communicate software designs, and when is it actually useful?

**Concepts:**
- What UML is: Unified Modeling Language — a standardized notation for drawing software structures and behaviors, not a design methodology
- Why it exists: software designs are hard to communicate in prose; diagrams with agreed-upon symbols remove ambiguity
- The two families of diagrams:
  - **Structure diagrams** — what a system *is*:
    - Class diagram: classes, their attributes, methods, and relationships (inheritance, composition, association)
    - Component diagram: how large components fit together and depend on each other
    - Package diagram: how code is organized into namespaces/modules
  - **Behavior diagrams** — what a system *does*:
    - Sequence diagram: how objects/components interact over time (who calls whom, in what order)
    - Activity diagram: workflow and decision logic (like a flowchart with richer notation)
    - Use case diagram: what a system does from a user's perspective
- The relationships that matter most in class diagrams:
  - Association: A uses B
  - Aggregation: A has a B (B can exist without A)
  - Composition: A owns a B (B cannot exist without A)
  - Inheritance: A is a B
  - Dependency: A depends on B (weakest relationship)
- Practical reality: most engineers use informal UML — whiteboards, rough sketches, tools like Mermaid or draw.io — not formal spec-compliant diagrams. The value is in the vocabulary and visual conventions, not strict notation compliance.
- When UML is worth reaching for: communicating a design to another person, documenting a system for future maintainers, thinking through relationships before writing code

**Tools — the honest landscape:** Unlike version control (where GitHub won), UML has no single dominant tool. The space splits along a workflow preference:
- **Mermaid** — text-based (you write a simple syntax, it renders the diagram). Free, open source, and already embedded in GitHub README rendering, Notion, and VS Code. The most natural fit if you think in markdown and git. Best for sequence diagrams and class diagrams. Start here.
- **draw.io / diagrams.net** — free, browser-based drag-and-drop. The standard free option when you need to draw something visually rather than code it. Integrates with VS Code and Google Drive.
- **Lucidchart** — the dominant paid team tool; widely used in corporate environments. More polished than draw.io; integrates with Confluence, Jira, and Slack. Worth knowing exists but probably overkill for your current context.

For your purposes: Mermaid is the right first tool — it produces diagrams-as-code, fits naturally in a markdown workflow, and is already available wherever you write documentation.

**Canonical reference:** University of Alberta "Object-Oriented Design" course (Coursera) — UML and modeling sections. For quick reference: uml-diagrams.org (free, comprehensive)

**Reflection prompt:** Draw a rough class/component diagram of your Era pipeline using whatever UML-inspired notation feels natural. Which diagram type captures the structure most clearly — a component diagram (showing script dependencies) or a sequence diagram (showing what happens during a `pull_doc` call)? Notice whether the act of drawing it surfaces any design decisions you hadn't made explicitly.

---

## Unit 10: Architectural Styles

**Core question:** How are large software systems structured, and what are the tradeoffs between different structural choices?

**Concepts:**
- What architecture means: the arrangement of components and the nature of their interactions
- Major architectural styles:
  - **Layered/N-tier**: components in horizontal layers; each layer only talks to adjacent layers (e.g., presentation → logic → data)
  - **Client-server**: a clear distinction between requesters and providers of service
  - **Event-driven**: components communicate by emitting and consuming events; no direct coupling
  - **Microservices**: independent deployable units with well-defined APIs; tradeoffs in complexity
  - **Pipe-and-filter**: data flows through a sequence of transformations (your pipeline is this)
  - **Service-oriented (SOA)**: services expose functionality over a network; the predecessor to microservices
- Architectural qualities: scalability, maintainability, testability, performance — how style affects each
- How to document and evaluate architecture using tradeoff analysis

**Canonical reference:** University of Alberta "Software Architecture" course (Coursera) — Architecture Tradeoff Analysis Method (ATAM) overview

**Reflection prompt:** Your Era pipeline is a pipe-and-filter architecture. What are the benefits of that choice for your use case? What would you lose if you converted it to an event-driven model where each script emitted events rather than being called directly?

---

## Unit 11: Code Smells and Anti-Patterns

**Core question:** How do you recognize bad design before it becomes a serious problem?

**Concepts:**
- What a code smell is: a symptom that suggests a design problem (not a bug)
- Common smells:
  - **Long method/function**: doing too many things; should be decomposed
  - **Large class/module**: too much responsibility; violates single responsibility
  - **Feature envy**: a function that uses another module's data more than its own
  - **Shotgun surgery**: one change requires edits in many places
  - **God object**: one component knows too much about everything else
  - **Primitive obsession**: using raw data types where a small abstraction would be cleaner
  - **Divergent change**: one module changes for many different reasons
- Refactoring: improving structure without changing behavior
- The relationship between smells, design principles (Unit 2), and design patterns (Unit 8)

**Canonical reference:** University of Alberta "Design Patterns" course — "Working with Design Patterns & Anti-patterns" module. Fowler's *Refactoring* catalog (refactoring.guru — free online)

**Reflection prompt:** Look at your pipeline's manifest-handling logic. Is it scattered across multiple scripts (shotgun surgery)? Is any one script doing manifest read + transform + write + logging (long method)? Name the smell and sketch the refactor.

---

## Unit 12: Modern Integration Patterns

**Core question:** How does software communicate across system boundaries, and how do newer patterns (like MCP) differ from traditional APIs?

**Concepts:**
- Synchronous vs. asynchronous communication patterns
- Polling vs. webhooks vs. event streaming
- REST vs. RPC vs. message-passing — when each is appropriate
- **MCP (Model Context Protocol)** as an architectural pattern:
  - Comparison to REST: both define a contract between a client and a service
  - Key difference: MCP is designed for AI model tool-use — the "caller" is a model, not deterministic code
  - How MCP standardizes tool discovery, invocation, and result handling
  - Why MCP matters for AI pipelines: composability without custom integration code
- Authentication patterns in integration: API keys, OAuth, token refresh flows
- Idempotency: why it matters when integrations can fail and retry

**Canonical reference:** MCP specification (modelcontextprotocol.io — free). University of Alberta "Service-Oriented Architecture" module — REST and web services sections.

**Reflection prompt:** Your pipeline currently uses the Google Drive and Docs APIs directly with OAuth. If you rebuilt `pull_doc` as an MCP tool, what would the tool contract look like? What would the model need to know to call it correctly?

---

## Unit 13: Systems Thinking and Design Evaluation

**Core question:** How do you reason about a whole system — including the parts you didn't build and the ways it will change?

**Concepts:**
- Systems thinking: emergent properties, feedback loops, unintended consequences
- Evolutionary architecture: designing for change over time, not just for today
- Technical debt: what it is, how it accrues, how to reason about when to pay it
- Fitness functions: how to measure whether a system has the qualities you care about
- Design review: how to evaluate your own system against the frameworks from Units 1–11
- The limits of architecture: organizational structure, Conway's Law, and why systems mirror their builders

**Canonical reference:** *Building Evolutionary Architectures* (Ford, Parsons, Kua) — Chapter 1 intro is free online. Conway's Law original paper (short, free online).

**Reflection prompt:** Apply Conway's Law to your situation: you're a solo builder. What does that predict about the architecture of your pipeline? What would change if Era became a team of three?

---

## Appendix: Topic Cross-Reference

| Topic | Primary Unit | Also appears in |
|---|---|---|
| Modularity | 2 | 4, 10, 11 |
| Specifications | 3 | 5, 7 |
| Abstract data types | 4 | 2, 3 |
| Testing | 5 | 3, 7 |
| Version control | 6 | 13 |
| API design | 7 | 8, 10, 12 |
| Design patterns | 8 | 2, 10, 11 |
| UML notation | 9 | 8, 10 |
| Architectural styles | 10 | 7, 12, 13 |
| Code smells | 11 | 2, 8 |
| MCP / integration | 12 | 7, 10 |
| Systems thinking | 13 | All |

---

## Suggested Pacing

**Fast track (conceptual fluency only):** Units 1–4 + 7 + 9 + 10 + 12. Skips testing depth and pattern catalogs. Best if your goal is to reason about system design, not write production-grade code.

**Full track:** All 13 units in order. ~3–4 hours per unit including reflection.

**Starting point if you've already shipped a real system:** Begin at Unit 3 (Specifications). Units 1–2 will feel like naming things you already know; Unit 3 is where the formal vocabulary starts adding real leverage.
