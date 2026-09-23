# Feature Specification: [FEATURE NAME]

**Feature Branch**: `[###-feature-name]`
**Created**: [DATE]
**Status**: Draft
**Input**: User description: "$ARGUMENTS"

---

# Purpose

This document defines **WHAT must be achieved and WHY it matters**.

It MUST describe:

* problem;
* expected behavior;
* inputs;
* outputs;
* rules;
* edge cases;
* failure expectations;
* measurable success criteria.

It MUST NOT prescribe implementation details unless they are genuine external constraints.

Avoid specifying:

* classes;
* inheritance;
* ABC;
* Protocol;
* design patterns;
* internal architecture;
* library choices;
* framework choices;
* specific algorithms;

unless the requirement itself genuinely depends on them.

Implementation decisions belong primarily in `plan.md`.

---

# Problem Statement *(mandatory)*

## Problem

[Describe the concrete problem being solved.]

## Why It Matters

[Explain why solving this problem is useful in the context of the current project or learning objective.]

## Current Situation

[Describe the current state before this feature exists.]

## Desired Outcome

[Describe the observable state after the feature is complete.]

---

# Inputs and Outputs *(mandatory)*

## Inputs

Describe what enters the system or feature.

| Input   | Description   | Required? | Constraints   |
| ------- | ------------- | --------: | ------------- |
| [input] | [description] |    Yes/No | [constraints] |

Do not describe implementation types unless required by the specification.

## Outputs

Describe observable outputs.

| Output   | Description   | Conditions      |
| -------- | ------------- | --------------- |
| [output] | [description] | [when produced] |

## Side Effects

[List observable side effects such as file creation, database writes, network requests, logging, or state changes.]

If none:

```text
None.
```

---

# Behavioral Rules *(mandatory)*

Define the rules that determine correct behavior.

* **BR-001**: [behavioral rule]
* **BR-002**: [behavioral rule]
* **BR-003**: [behavioral rule]

Rules MUST describe behavior, not implementation.

Prefer:

```text
The feature MUST ignore directories when discovering files.
```

instead of:

```text
The implementation MUST call Path.is_file().
```

The first specifies behavior.

The second specifies implementation.

---

# User / Engineering Scenarios & Testing *(mandatory)*

Not every Data Engineering exercise naturally represents an end-user journey.

Use the most appropriate scenario type:

```text
USER SCENARIO
```

for user-facing behavior,

or:

```text
ENGINEERING SCENARIO
```

for pipelines, collectors, transformations, storage, infrastructure or learning exercises.

Do NOT invent artificial users merely to satisfy the template.

---

## Scenario 1 — [Brief Title] (Priority: P1)

[Describe the behavior or engineering outcome in plain language.]

**Why this priority**:
[Explain why this is the most important behavior.]

**Independent Verification**:
[Explain how this behavior can be verified independently.]

### Acceptance Scenarios

1. **Given** [initial condition], **When** [event/action], **Then** [observable result].
2. **Given** [initial condition], **When** [event/action], **Then** [observable result].

---

## Scenario 2 — [Brief Title] (Priority: P2)

[Describe the behavior.]

**Why this priority**:
[Reason.]

**Independent Verification**:
[Verification.]

### Acceptance Scenarios

1. **Given** [condition], **When** [action], **Then** [result].

---

[Add scenarios only when they represent meaningful independent behavior.]

---

# Edge Cases *(mandatory)*

Identify boundaries before implementation.

Consider where applicable:

* empty input;
* missing input;
* invalid input;
* duplicate input;
* unexpected format;
* boundary values;
* casing;
* malformed data;
* inaccessible resource;
* partial failure;
* repeated execution;
* empty result;
* large input.

Document actual relevant cases:

| Edge Case   | Expected Behavior   |
| ----------- | ------------------- |
| [condition] | [expected behavior] |

Do NOT invent handling for cases outside the current scope.

---

# Failure Scenarios *(mandatory)*

Identify meaningful ways the feature can fail.

| Failure   | Expected Observable Behavior |
| --------- | ---------------------------- |
| [failure] | [expected behavior]          |

The specification should define **what behavior is expected**, not necessarily how recovery will be implemented.

Detailed recovery mechanisms belong in `plan.md`.

---

# Requirements *(mandatory)*

## Functional Requirements

* **FR-001**: The feature MUST [specific observable capability].
* **FR-002**: The feature MUST [specific observable behavior].
* **FR-003**: The feature MUST [specific rule].

Every functional requirement MUST be:

* testable;
* unambiguous;
* traceable to the problem;
* implementation-independent where possible.

If essential information is missing:

```text
[NEEDS CLARIFICATION: specific question]
```

Do not silently invent important requirements.

---

# Data Concepts *(include when applicable)*

Describe relevant data concepts without defining implementation classes.

| Concept   | Meaning   | Important Attributes / Rules |
| --------- | --------- | ---------------------------- |
| [concept] | [meaning] | [attributes/rules]           |

For example, describe:

```text
Collected File
```

as a domain/data concept.

Do NOT automatically convert it into:

```text
CollectedFile class
```

That decision belongs to design.

---

# Non-Functional Requirements *(when applicable)*

Only include requirements justified by the problem.

## Performance

* **NFR-PERF-001**: [measurable performance requirement]

If no performance target is known, state:

```text
No optimization target is defined yet.
A baseline will be measured before optimization decisions.
```

## Memory

* **NFR-MEM-001**: [constraint or expected behavior]

## Reliability

* **NFR-REL-001**: [reliability requirement]

## Idempotency

Describe expected repeated-execution behavior when applicable.

## Observability

Describe what must be observable from outside the feature when applicable.

## Security

Describe security requirements when applicable.

## Cost

Describe cost constraints when relevant.

Do NOT invent production-grade requirements for an early learning exercise.

---

# Scope *(mandatory)*

## In Scope

* [behavior]
* [behavior]

## Out of Scope

* [explicitly excluded behavior]
* [future concern]
* [future architecture]

Out-of-scope items SHOULD prevent future roadmap concepts from leaking into the current implementation.

---

# Success Criteria *(mandatory)*

Success criteria MUST be measurable or objectively verifiable.

## Functional Success

* **SC-001**: [observable outcome]
* **SC-002**: [observable outcome]

## Engineering Success

When relevant:

* **SC-003**: Expected edge cases produce the specified behavior.
* **SC-004**: Failure scenarios are observable as specified.
* **SC-005**: Repeated execution behaves as specified.

## Learning Success

For learning features, define what the student must be able to explain or demonstrate.

Examples:

* **LS-001**: Student can explain the feature's input → processing → output flow.
* **LS-002**: Student can explain relevant I/O operations.
* **LS-003**: Student can reproduce the core implementation without copying a complete solution.
* **LS-004**: Student can explain important edge cases and failure modes.

Learning success criteria MUST NOT require concepts that have not yet been introduced.

---

# Assumptions

Document reasonable assumptions explicitly.

* [assumption]
* [assumption]

Assumptions MUST NOT silently introduce architectural decisions.

---

# Dependencies

List genuine external dependencies or prerequisites.

Examples:

* existing data source;
* filesystem access;
* database availability;
* API credentials;
* previously completed feature.

Do NOT list future architectural components merely because they exist in `ARCHITECTURE.md`.

If none:

```text
None.
```

---

# Constraints

Document constraints imposed by the problem or environment.

Examples:

* supported input format;
* operating environment;
* required compatibility;
* regulatory constraint;
* learning-stage restriction.

A learning constraint is valid.

Example:

```text
This feature must initially be implemented using fundamental Python and pathlib without Pandas.
```

This is different from prescribing an internal architecture because it defines the pedagogical boundary of the exercise.

---

# Clarifications

Use this section to record resolved specification questions.

| Question   | Resolution |
| ---------- | ---------- |
| [question] | [decision] |

Unresolved questions MUST remain marked `NEEDS CLARIFICATION`.

---

# Specification Quality Gate

Before `/speckit-plan`, verify:

### Problem

* [ ] The concrete problem is defined.
* [ ] The desired outcome is observable.

### Behavior

* [ ] Inputs are defined.
* [ ] Outputs are defined.
* [ ] Behavioral rules are defined.
* [ ] Relevant edge cases are identified.
* [ ] Relevant failures are identified.

### Requirements

* [ ] Functional requirements are testable.
* [ ] Requirements describe WHAT rather than HOW.
* [ ] Important ambiguities are marked `NEEDS CLARIFICATION`.
* [ ] Scope and out-of-scope boundaries are explicit.

### Engineering

* [ ] Relevant I/O expectations are visible.
* [ ] Repeated execution behavior is defined when applicable.
* [ ] Performance requirements are measurable or deferred to baseline measurement.
* [ ] No unsupported scalability requirement has been invented.
* [ ] No unnecessary production requirement has been introduced.

### Learning

* [ ] Current learning objective is explicit when applicable.
* [ ] The specification does not reveal the complete implementation.
* [ ] Concepts beyond the current learning stage are not required.
* [ ] Success can generate evidence for the Skills Matrix.

### Architecture

* [ ] No speculative architecture is prescribed.
* [ ] No class hierarchy is prescribed without being a true external constraint.
* [ ] No ABC/Protocol is prescribed merely for extensibility.
* [ ] No Design Pattern is prescribed without a requirement-level reason.
* [ ] Future versions from `ARCHITECTURE.md` have not leaked into current scope.

If any applicable item fails, revise the specification before `/speckit-plan`.
