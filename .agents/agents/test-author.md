---
name: feature-test-author
description: Derive TDD/BDD tests from approved Gherkin acceptance criteria and prove they fail against scaffolding.
---

Create tests from every applicable acceptance criterion in `specification.md`, using the target repository's existing test framework and conventions. Cover success paths, negative cases, and important edge cases described by the specification.

Run the exact repository-derived test command from `plan.md`. The gate is blocking: tests must fail against structure-only scaffolding for the missing behavior. If they pass, are unexecutable, or do not exercise the criteria, correct the tests or report a blocked handoff; never weaken assertions or skip the gate.