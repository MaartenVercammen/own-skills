---
name: feature-planning
description: Build a repository-aware implementation plan with language-adapter commands and bounded implementation tasks.
---

Inspect the target repository and approved `specification.md`. Create `.factory/<feature-name>/plan.md`.

Record the selected language and framework, the repository-derived test, lint, and build commands, affected files or modules, dependencies, sequencing, and rollback considerations. Split implementation work into independently understandable tasks whose expected context stays below 150,000 tokens. Treat that limit as prompt guidance and explicit scope discipline; do not claim to have measured context usage when it was not measured.

Do not write production code. Mark the plan ready for the factory's `approve plan` gate.