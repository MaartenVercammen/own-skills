---
name: feature-factory
description: Orchestrate an end-to-end, language-aware feature development workflow from user discovery through specification, planning, TDD implementation, reviews, PR-ready handoff, and approved retrospective improvements.
---

# Feature Factory

Use this skill when the user wants a new product feature, code-generation workflow, or substantial implementation carried out like an agile team.

## Operating contract

The factory is a sequential workflow. Do not skip a gate, silently infer an approval, or begin implementation before the required artifact is approved.

1. Start with the `grilling` skill. Ask the user what they want to create and build a mental map of the product or feature through round-based questions. Do not create project files until the user confirms shared understanding.
2. Create `.factory/<feature-name>/glossary.md` and `mental-map.md`. Define domain terms and record the agreed product shape.
3. Ask the `specification` agent to create `specification.md`. It must contain requirements and acceptance criteria in Gherkin/BDD syntax.
4. Present the specification and wait for an explicit, scoped `approve specification` response. If rejected, revise the owning artifacts and invalidate all downstream artifacts and approvals.
5. Ask the `planning` agent to create `plan.md`. The plan must select a repository-derived language adapter and record the exact test, build, and lint commands. Keep each implementation task below the 150,000-token context limit; this workflow uses prompt guidance and explicit task scope rather than pretending to measure tokens precisely.
6. Present the plan and wait for `approve plan`. Rejection rewinds downstream work.
7. Ask the `scaffolding` agent to create compile-safe structure only: classes, objects, modules, interfaces, constructors, configuration placeholders, and startup entry points. It must not add business behavior.
8. Ask the `test-author` agent to derive tests from the Gherkin acceptance criteria. Run the repository-defined test command and require the tests to fail against the scaffolding. If they do not fail, block the workflow and correct the tests or scaffolding before continuing.
9. Ask the `implementation` agent to implement the plan against the failing tests. Run the repository-defined checks and require them to pass. Do not use universal commands when the repository provides its own conventions.
10. Ask the `specification-reviewer` agent to review the implementation against `specification.md`. Fix findings and rerun the review until it passes.
11. Ask the `standards-reviewer` agent to check coding standards and best practices after specification review passes. Fix findings and rerun the review until it passes.
12. Prepare a PR-ready handoff containing a proposed branch name, commit summary, PR title and body, changed-file summary, validation results, and remaining human actions. Do not submit a remote PR unless a configured integration explicitly exists.
13. Present the handoff and wait for `approve PR-ready output`. Rejection rewinds the PR handoff and any dependent work.
14. Ask the `retrospective` agent to create `retrospective.md`, including evidence, failure modes, proposed reusable skill or guideline changes, and expected benefit. Present it and wait for `approve retrospective`.

## Workspace and decision log

Use these stable files under `.factory/<feature-name>/`:

- `glossary.md`
- `mental-map.md`
- `specification.md`
- `plan.md`
- `retrospective.md`
- `decisions.md`

Each Markdown artifact uses minimal front matter with `feature`, `artifact`, `status`, and `updated_stage`. Append dated approvals, rejections, and rewind reasons to `decisions.md`; conversation history alone is not an approval record.

## Language adapter contract

Inspect the target repository before selecting a toolchain. Record the selected language, framework, test command, lint command, and build command in `plan.md`. Prefer existing repository conventions. If any required fact cannot be determined, pause and ask the user instead of guessing or applying a built-in default.

## Agent roles

Use the focused prompts in `agents/`:

- `specification.md`
- `planning.md`
- `scaffolding.md`
- `test-author.md`
- `implementation.md`
- `specification-reviewer.md`
- `standards-reviewer.md`
- `retrospective.md`

The factory skill owns orchestration and approvals; these agents own the work at each gate.

## Completion criteria

The feature is complete only when all required automated checks pass, both implementation reviews pass, the PR-ready handoff is approved, the retrospective report is approved, and the decision log records the outcomes.