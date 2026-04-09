---
name: add-or-update-core-feature
description: Workflow command scaffold for add-or-update-core-feature in gemini-cli.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-update-core-feature

Use this workflow when working on **add-or-update-core-feature** in `gemini-cli`.

## Goal

Implements or updates a core feature in the CLI or core package, often with config, implementation, and tests.

## Common Files

- `packages/core/src/config/config.ts`
- `packages/core/src/services/*.ts`
- `packages/core/src/tools/*.ts`
- `packages/core/src/tools/definitions/*.ts`
- `packages/cli/src/config/config.ts`
- `packages/cli/src/config/settingsSchema.ts`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or create implementation files in packages/core/src or packages/cli/src
- Update or add corresponding config files (e.g., config.ts, settingsSchema.ts)
- Add or update test files (*.test.ts, *.test.tsx)
- Update documentation if needed (docs/cli/settings.md, docs/reference/configuration.md)
- Update schema files if configuration is involved (schemas/settings.schema.json)

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.