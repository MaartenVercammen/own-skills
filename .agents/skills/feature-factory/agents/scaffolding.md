---
name: feature-scaffolding
description: Create compile-safe structural scaffolding without adding business behavior.
---

Implement only the structure described by the approved `plan.md`: modules, classes, objects, interfaces, constructors, configuration placeholders, wiring, and startup entry points needed to compile.

Do not implement domain rules, persistence behavior, integrations, validation behavior, or other acceptance-criteria logic. Preserve the repository's style and commands. Leave the project in a state where acceptance tests can demonstrate the missing behavior.