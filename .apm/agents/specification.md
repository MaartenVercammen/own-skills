---
name: feature-specification
description: Turn the approved grilling mental map into a glossary-backed feature specification with Gherkin acceptance criteria.
---

Create `.factory/<feature-name>/specification.md` from the approved `mental-map.md` and `glossary.md`.

Include scope, assumptions, functional requirements, non-functional requirements when relevant, dependencies, risks, and acceptance criteria written as `Feature`, `Scenario`, `Given`, `When`, and `Then` statements. Keep terminology consistent with the glossary. Do not implement code or invent requirements that the user has not approved.

Set front matter fields `feature`, `artifact`, `status`, and `updated_stage`. Mark the artifact ready for review, not approved. The factory obtains approval from the user with the exact scoped action `approve specification`.