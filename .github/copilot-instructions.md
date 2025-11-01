# GitHub Copilot Instructions

This document provides specific instructions for GitHub Copilot when working with this TypeScript project boilerplate.

## Project Overview

This is a modern TypeScript project boilerplate for Node.js environments with pnpm, Biome, Vitest, and strict type checking.

## Essential Commands

- **Install dependencies**: `pnpm install`
- **Build**: `pnpm build` (compiles TypeScript to `dist/`)
- **Test**: `pnpm test` (runs Vitest)
- **Format**: `pnpm format` (auto-formats with Biome)
- **Lint and fix**: `pnpm biome:fix`
- **Type check**: `pnpm check:types`
- **All checks**: `pnpm check`

## Key Guidelines

### Package Manager
- **Always use pnpm**, never npm or yarn
- Run `pnpm install` after cloning or updating package.json

### Code Style
- Use TypeScript with strict type checking (enabled)
- Import statements must use `.js` extensions for ESM modules (e.g., `import { add } from "./index.js"`)
- Follow the existing code patterns in `src/`
- Leverage TypeScript type inference where appropriate
- Add explicit types for public APIs and function parameters
- Avoid `any` types unless absolutely necessary

### Testing
- Test framework: Vitest (Jest-like API)
- Co-locate tests with source files: `feature.ts` → `feature.test.ts`
- Use `describe()`, `it()`, and `expect()` from Vitest
- Always run `pnpm test` after making changes

### Formatting and Linting
- This project uses Biome (not ESLint or Prettier)
- Auto-format: `pnpm format`
- Auto-fix linting: `pnpm biome:fix`
- Run `pnpm check` before committing

### Building
- Build command: `pnpm build`
- Output directory: `dist/` (gitignored, don't commit)
- Always verify builds succeed after changes

## Workflow

1. Install dependencies: `pnpm install`
2. Make code changes in `src/`
3. Add/update tests co-located with source files
4. Format code: `pnpm format`
5. Fix linting: `pnpm biome:fix`
6. Run all checks: `pnpm check`
7. Run tests: `pnpm test`
8. Build: `pnpm build`

## Common Patterns

### Adding a new module
1. Create `src/module-name.ts`
2. Create `src/module-name.test.ts`
3. Use `.js` extensions in imports
4. Export types and functions explicitly

### TypeScript Configuration
- Extends `@total-typescript/tsconfig`
- Strict mode enabled
- ESNext module resolution
- Outputs to `dist/`

## What NOT to Do

- Don't use npm or yarn (use pnpm only)
- Don't commit `dist/` directory (it's gitignored)
- Don't skip the build step
- Don't ignore linting errors
- Don't forget to update tests
- Don't omit `.js` extensions in imports

## Additional Resources

For more detailed information, see [AGENTS.md](../AGENTS.md) in the repository root.
