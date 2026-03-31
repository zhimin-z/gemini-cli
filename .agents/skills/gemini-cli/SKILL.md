```markdown
# gemini-cli Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you how to contribute to the `gemini-cli` TypeScript codebase, which provides a CLI and core library for interacting with Gemini tools and configurations. You'll learn the project's coding conventions, how to add features, update tools, manage configuration schemas, write and update tests, and maintain documentation and changelogs using structured workflows and commands.

## Coding Conventions

### File Naming

- Source files: `camelCase` (e.g., `toolRegistry.ts`, `settingsSchema.ts`)
- Test files: Suffix `.test.ts` or `.test.tsx` (e.g., `toolRegistry.test.ts`)
- Documentation: Markdown in `docs/` (e.g., `settings.md`, `configuration.md`)

### Import Style

- **Relative imports** are used throughout:
  ```typescript
  import { getTool } from './toolRegistry';
  import config from '../config/config';
  ```

### Export Style

- **Mixed**: Both named and default exports are used.
  ```typescript
  // Named export
  export function getTool(name: string) { ... }

  // Default export
  export default config;
  ```

### Commit Messages

- **Conventional commits**: Prefixes like `fix`, `feat`, `refactor`, `test`, `docs`
- Example:  
  ```
  feat: add support for custom tool registry in core
  fix: handle missing config file gracefully
  ```

## Workflows

### Add or Update Core Feature
**Trigger:** When adding or significantly updating a core or CLI feature  
**Command:** `/add-feature`

1. Edit or create implementation files in `packages/core/src` or `packages/cli/src`
2. Update or add config files (e.g., `config.ts`, `settingsSchema.ts`)
3. Add or update test files (`*.test.ts`, `*.test.tsx`)
4. Update documentation if needed (`docs/cli/settings.md`, `docs/reference/configuration.md`)
5. Update schema files if configuration is involved (`schemas/settings.schema.json`)

**Example:**
```typescript
// packages/core/src/services/newFeature.ts
export function newFeature() { ... }
```
```typescript
// packages/core/src/services/newFeature.test.ts
import { newFeature } from './newFeature';
test('newFeature works', () => { ... });
```

---

### Add or Update Tool
**Trigger:** When adding a new tool or updating an existing tool's logic  
**Command:** `/add-tool`

1. Edit or create tool implementation in `packages/core/src/tools/`
2. Update or add tool declaration in `packages/core/src/tools/definitions/`
3. Update tool registry or tool-names files if registering a new tool
4. Add or update test files for the tool (`*.test.ts`)
5. Update base-declarations or model-family-sets if needed

**Example:**
```typescript
// packages/core/src/tools/myTool.ts
export function myTool() { ... }
```
```typescript
// packages/core/src/tools/definitions/myToolDef.ts
export interface MyToolDef { ... }
```

---

### Config Schema Update
**Trigger:** When adding or changing a configuration option  
**Command:** `/update-config-schema`

1. Edit settings schema (`schemas/settings.schema.json`)
2. Update config files (`packages/cli/src/config/settingsSchema.ts`, `packages/core/src/config/config.ts`)
3. Update documentation (`docs/cli/settings.md`, `docs/reference/configuration.md`)

**Example:**
```json
// schemas/settings.schema.json
{
  "properties": {
    "newOption": { "type": "string", "description": "A new config option" }
  }
}
```

---

### Feature with Tests and Docs
**Trigger:** When adding a new user-facing feature or enhancement  
**Command:** `/feature`

1. Implement the feature in source files
2. Add or update test files (`*.test.ts`, `*.test.tsx`)
3. Update documentation files to describe the new feature

---

### Changelog Update
**Trigger:** When publishing a new release or preview version  
**Command:** `/changelog`

1. Edit the appropriate changelog file (`docs/changelogs/latest.md` or `docs/changelogs/preview.md`)

---

### Bugfix with Test
**Trigger:** When fixing a bug and ensuring it is tested  
**Command:** `/fix-bug`

1. Edit the source file to fix the bug
2. Edit or add a test file (`*.test.ts`, `*.test.tsx`) to cover the bug scenario

**Example:**
```typescript
// packages/core/src/services/buggyService.ts
export function fixedService() { /* bug fixed */ }
```
```typescript
// packages/core/src/services/buggyService.test.ts
test('bug is fixed', () => { ... });
```

## Testing Patterns

- **Framework:** [Vitest](https://vitest.dev/)
- **Test files:**  
  - Suffix: `.test.ts` or `.test.tsx`
  - Located alongside source files or in the same directory

**Example:**
```typescript
// packages/core/src/tools/toolRegistry.test.ts
import { getTool } from './toolRegistry';

test('getTool returns correct tool', () => {
  expect(getTool('example')).toBeDefined();
});
```

## Commands

| Command            | Purpose                                                      |
|--------------------|--------------------------------------------------------------|
| /add-feature       | Add or update a core or CLI feature                          |
| /add-tool          | Add or update a tool in the core                             |
| /update-config-schema | Update configuration schemas and related documentation     |
| /feature           | Add a new user-facing feature with tests and docs            |
| /changelog         | Update the changelog for a new release or preview            |
| /fix-bug           | Fix a bug and add or update a test to cover the fix          |
```