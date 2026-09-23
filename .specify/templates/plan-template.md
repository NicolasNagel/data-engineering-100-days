# Implementation Plan: [FEATURE]

**Branch**: `[###-feature-name]` | **Date**: [DATE] | **Spec**: [link]
**Input**: Feature specification from `/specs/[###-feature-name]/spec.md`

**Note**: This template is filled in by the `/speckit-plan` command; its definition describes the execution workflow.

---

## Summary

[Extract from feature spec: primary requirement + simplest viable technical approach supported by current requirements]

The plan MUST describe the simplest architecture capable of satisfying the current specification.

Future architectural versions MUST NOT be introduced solely because they are expected later in the roadmap.

---

## Technical Context

<!--
  ACTION REQUIRED: Replace the content in this section with the technical details
  for the project.

  Unknown information MUST be marked NEEDS CLARIFICATION rather than invented.

  Technical choices MUST follow the current learning stage and Constitution.
-->

**Language/Version**: [e.g., Python 3.13 or NEEDS CLARIFICATION]

**Primary Dependencies**: [libraries actually required by the current problem or N/A]

**Storage**: [files, PostgreSQL, object storage, N/A, or NEEDS CLARIFICATION]

**Testing**: [e.g., pytest or NEEDS CLARIFICATION]

**Target Platform**: [e.g., local Windows development, Linux container, cloud or NEEDS CLARIFICATION]

**Project Type**: [e.g., script/library/CLI/data-pipeline/web-service or NEEDS CLARIFICATION]

**Input / Output**: [primary inputs and expected outputs]

**I/O Profile**: [filesystem/network/database/object storage/memory materialization or N/A]

**Performance Goals**: [measurable requirement when one exists; otherwise establish baseline before optimization]

**Memory Constraints**: [known constraints, expected behavior, or NEEDS CLARIFICATION]

**Scale/Scope**: [current expected volume and relevant 10x scenario]

**Idempotency**: [required behavior on repeated execution or N/A with justification]

**Failure Detection**: [how failures become observable]

**Recovery Strategy**: [expected recovery behavior or N/A at the current learning stage]

**Cost Considerations**: [relevant compute/storage/network/request/operational costs or N/A]

**Observability**: [logging/metrics/tracing requirements appropriate to the current stage]

---

## Constitution Check

> **GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.**

The plan MUST be checked against Principles **I–XVIII** of `.specify/memory/constitution.md`.

The Constitution is authoritative.

### Learning and Implementation

* [ ] **I — Fundamentals Before Tools**
  The plan starts from the underlying engineering problem rather than from a tool.

* [ ] **II — Student Writes the Code**
  Learning implementation remains the student's responsibility.

* [ ] **III — Escalation Before Full Solution**
  The plan does not depend on the AI immediately producing complete learning implementations.

* [ ] **IV — Theory → Code → Review**
  The planned work preserves the learning sequence.

* [ ] **V — Logic Before Abstraction**
  Inputs, outputs, rules, failures, algorithm and simple implementation precede sophisticated abstractions.

* [ ] **VI — No Premature Knowledge**
  Concepts are not required before they are pedagogically introduced or justified by the problem.

### Engineering

* [ ] **VII — I/O First**
  Relevant reads, writes, network calls and materialization are identified.

* [ ] **VIII — Observability by Design**
  Failure detection and appropriate operational visibility are considered.

* [ ] **IX — Cost Is an Architectural Requirement**
  Relevant cost dimensions are identified where applicable.

* [ ] **X — Measure Before Optimize**
  Performance claims require measurement or an explicit future baseline.

* [ ] **XI — Simplicity Before Distribution**
  Distributed infrastructure is not introduced without demonstrated need.

* [ ] **XII — Idempotency and Failure**
  Repeated execution, partial failure and recovery are considered where applicable.

* [ ] **XIII — Debugging Before Fixing**
  The plan preserves investigation and root-cause reasoning.

### Evidence and Learning

* [ ] **XIV — Evidence-Based Progress**
  Tasks can generate observable evidence of learning.

* [ ] **XV — Explain Before Accept**
  Important decisions must be explainable by the student.

* [ ] **XVI — No Copy-Paste Learning**
  The plan does not rely on copying unexplained implementations.

* [ ] **XVII — AI Must Preserve Learning**
  AI assistance does not remove the reasoning or implementation work being learned.

### Object-Oriented Design

* [ ] **XVIII — Progressive Object-Oriented Design**
  OOP is introduced progressively and only when appropriate to the current learning stage and problem.

If the plan proposes any of the following:

* classes;
* inheritance;
* ABC;
* Protocol;
* polymorphic interfaces;
* Dependency Injection;
* Repository;
* Strategy;
* Adapter;
* Factory;
* other design patterns or architectural abstractions;

the plan MUST answer:

1. What concrete design problem exists?
2. Why is the current/simple implementation insufficient?
3. What responsibility, state, variation, substitution, testability or coupling problem is being addressed?
4. What simpler alternative was considered?
5. What additional complexity does the abstraction introduce?
6. How will the before/after designs be compared?
7. Can the abstraction be removed if it does not provide proportional benefit?

A statement such as:

> "This is best practice."

is NOT sufficient justification.

A statement such as:

> "We will need this later."

is NOT sufficient justification.

---

## Mandatory Engineering Questions

Before the plan passes the Constitution Check, answer the following or explicitly mark them N/A with justification:

1. Is the proposed behavior correct relative to the specification?
2. What are the inputs and outputs?
3. Is the operation idempotent?
4. What is the I/O profile?
5. What is the expected memory behavior?
6. How are failures detected?
7. How does recovery work?
8. What does the solution cost?
9. What happens at 10x the current volume?
10. What happens if it runs twice?
11. How will it be tested?
12. What is the main known or expected bottleneck?
13. Is that bottleneck measured or assumed?
14. Which important decisions are reversible?
15. What complexity is being added and why?

For early learning cycles, some answers MAY be conceptual rather than production implementations.

---

## Architecture Evolution Check

The plan MUST NOT implement a future architecture merely because it appears in `ARCHITECTURE.md`.

Use:

```text
IMPLEMENT
↓
OBSERVE
↓
IDENTIFY LIMITATION
↓
UNDERSTAND THE PROBLEM
↓
STUDY THE CONCEPT
↓
REFACTOR
↓
COMPARE
↓
CONSOLIDATE
```

If a future architectural component is proposed, document the current requirement that makes it necessary.

Examples include:

* common Collector interfaces;
* `CollectionResult`;
* Validator / Transformer separation;
* Storage abstractions;
* Loader abstractions;
* CDC/SCD strategies;
* HTTP strategies;
* Pipeline orchestration.

`ARCHITECTURE.md` is a map of possible evolution, not a mandatory target architecture.

---

## Project Structure

### Documentation (this feature)

```text
specs/[###-feature]/
├── plan.md              # This file (/speckit-plan command output)
├── research.md          # Phase 0 output (/speckit-plan command)
├── data-model.md        # Phase 1 output when applicable
├── quickstart.md        # Phase 1 output when applicable
├── contracts/           # Phase 1 output when applicable
└── tasks.md             # Phase 2 output (/speckit-tasks command)
```

Documentation artifacts that are not relevant to the current feature SHOULD NOT be created merely because they appear in this template.

### Source Code (repository root)

<!--
  ACTION REQUIRED:

  Replace this placeholder with the smallest concrete structure required by
  the current feature.

  Do NOT create directories such as models/, services/, repositories/,
  interfaces/, factories/, strategies/, adapters/ or similar merely because
  they may be useful in later versions.

  Structure must emerge from current responsibilities.
-->

```text
[CONCRETE STRUCTURE FOR CURRENT FEATURE]
```

**Structure Decision**:
[Explain why this is the simplest structure appropriate to the current requirements and learning stage.]

---

## Design Decisions

For every significant technical or architectural decision, record:

**Problem**: [What concrete problem requires a decision?]

**Options Considered**: [What reasonable alternatives were considered?]

**Decision**: [What was selected?]

**Why**: [Why does it fit current requirements?]

**Trade-offs**: [What is gained and lost?]

**Reversibility**: [How difficult would it be to change later?]

**Evidence Needed**: [What test, measurement or implementation result can validate the decision?]

---

## Complexity Tracking

> **Fill ONLY if the Constitution Check identifies complexity that must be explicitly justified.**

| Complexity / Violation | Concrete Problem                                           | Why Needed Now        | Simpler Alternative | Why Rejected          | Evidence                        |
| ---------------------- | ---------------------------------------------------------- | --------------------- | ------------------- | --------------------- | ------------------------------- |
| [e.g., Protocol]       | [multiple implementations require structural substitution] | [current requirement] | [duck typing]       | [specific limitation] | [test/refactor comparison]      |
| [e.g., Repository]     | [domain logic is tightly coupled to persistence]           | [current requirement] | [direct access]     | [specific limitation] | [testability/coupling evidence] |

If there is no justified additional complexity:

```text
No Constitution violations or exceptional complexity.
```

---

## Post-Design Constitution Re-check

After Phase 1 design, repeat the Constitution Check.

Specifically verify that research or design did NOT introduce:

* unnecessary dependencies;
* premature classes;
* speculative interfaces;
* unjustified patterns;
* unnecessary distributed infrastructure;
* premature optimization;
* hidden I/O;
* unmeasured performance claims;
* unnecessary architectural layers.

Any new complexity introduced during design MUST be added to **Complexity Tracking** or removed before task generation.
