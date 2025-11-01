# GitHub Copilot Instructions

This document provides guidance for GitHub Copilot, AI coding agents, and automated tools working with this TypeScript project boilerplate.

## Project Overview

This is a modern TypeScript project boilerplate designed for Node.js environments. It includes essential tooling for formatting, linting, testing, and type checking.

### Key Technologies

- **TypeScript 5.x**: Modern TypeScript with strict type checking enabled
- **pnpm**: Fast, disk space-efficient package manager
- **Biome**: Fast formatter and linter (replaces ESLint + Prettier)
- **Vitest**: Modern test framework with Vite integration
- **Husky**: Git hooks for pre-commit validation

## Project Structure

```
.
├── src/                 # Source code directory
│   ├── index.ts        # Main entry point
│   ├── index.test.ts   # Tests (co-located with source)
│   └── vite.config.mts # Vitest configuration
├── dist/               # Build output (generated, not in git)
├── package.json        # Project metadata and scripts
├── tsconfig.json       # TypeScript configuration
├── biome.json          # Biome formatter/linter configuration
└── pnpm-lock.yaml      # Dependency lock file
```

## Available Commands

### Development
- `pnpm install` - Install dependencies (run after cloning or updating package.json)
- `pnpm build` - Compile TypeScript to JavaScript in `dist/`
- `pnpm test` - Run all tests with Vitest
- `pnpm check` - Run all checks (formatting, linting, type checking)

### Code Quality
- `pnpm format` - Auto-format code with Biome
- `pnpm biome:fix` - Fix linting issues automatically
- `pnpm biome:fix-unsafe` - Fix linting issues including potentially unsafe fixes
- `pnpm check:ci` - Check formatting/linting in CI mode (no auto-fix)
- `pnpm check:types` - Run TypeScript type checking without emitting files
- `pnpm lint` - Check code for linting issues (no auto-fix)

## Guidelines for AI Agents

### Before Making Changes

1. **Always install dependencies first**: Run `pnpm install` after cloning or if package.json has changed
2. **Run tests to understand current state**: Execute `pnpm test` to see existing test coverage
3. **Check build works**: Run `pnpm build` to ensure the project compiles
4. **Run linting/formatting**: Execute `pnpm check` to see the current code quality state

### Making Code Changes

1. **Follow existing patterns**: Examine existing code in `src/` to match style and structure
2. **Add tests for new code**: Place test files alongside source files (e.g., `feature.ts` → `feature.test.ts`)
3. **Use TypeScript properly**: 
   - Leverage type inference where appropriate
   - Add explicit types for public APIs and function parameters
   - Avoid `any` types unless absolutely necessary
4. **Import with .js extensions**: ESM modules require `.js` extensions even for `.ts` files (e.g., `import { add } from "./index.js"`)

### Testing

- **Test framework**: Vitest (similar to Jest API)
- **Test location**: Co-locate tests with source files in `src/`
- **Running tests**: `pnpm test` (runs all tests)
- **Test structure**: Use `describe()` and `it()` blocks
- **Assertions**: Use Vitest's `expect()` API

Example test:
```typescript
import { describe, expect, it } from "vitest";
import { myFunction } from "./index.js";

describe("myFunction", () => {
  it("should do something", () => {
    expect(myFunction(input)).toBe(expectedOutput);
  });
});
```

### After Making Changes

1. **Format code**: Run `pnpm format` to auto-format
2. **Fix linting issues**: Run `pnpm biome:fix` to auto-fix linting
3. **Run type checking**: Execute `pnpm check:types` to catch type errors
4. **Run all checks**: Execute `pnpm check` to ensure everything passes
5. **Run tests**: Execute `pnpm test` to verify functionality
6. **Build the project**: Run `pnpm build` to ensure it compiles successfully

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

## Common Pitfalls to Avoid

1. **Don't use npm or yarn**: This project uses pnpm exclusively
2. **Don't skip the build step**: Always verify `pnpm build` succeeds
3. **Don't ignore linting errors**: Run `pnpm check` and address all issues
4. **Don't forget test updates**: Update or add tests when changing functionality
5. **Don't commit generated files**: The `dist/` directory is gitignored and should not be committed
6. **Don't omit `.js` extensions in imports**: Required for ESM modules

## Updating Dependencies

When updating dependencies:

1. **Check for vulnerabilities**: Run `pnpm audit` after updates
2. **Update lock file**: Use `pnpm install` to update `pnpm-lock.yaml`
3. **Test after updates**: Always run `pnpm test` and `pnpm build` after updating dependencies
4. **Check for breaking changes**: Review changelogs for major version updates

## Configuration Files

### tsconfig.json
TypeScript configuration extends `@total-typescript/tsconfig`. Key settings:
- Strict mode enabled
- ESNext module resolution
- Outputs to `dist/`

### biome.json
Biome configuration for formatting and linting. Modify this file to adjust:
- Code formatting rules
- Linting rules
- File include/exclude patterns

### src/vite.config.mts
Vitest configuration. Modify this to:
- Adjust test environment settings
- Configure test pools
- Add test setup files

## Integration with CI/CD

This boilerplate includes GitHub Actions workflows. When making changes:
- The `check:ci` script is designed for CI environments (no auto-fix)
- Tests run automatically on push/PR
- All checks must pass before merging

## Version Requirements

- **Node.js**: Use the version specified in `mise.toml` or `.nvmrc` (if present)
- **pnpm**: Version managed by corepack (see `packageManager` field in package.json)
- **TypeScript**: Version specified in package.json devDependencies

## Questions or Issues?

If you encounter unexpected behavior or need clarification:
1. Check existing code patterns in `src/`
2. Review the error messages carefully
3. Consult the documentation for the specific tool (TypeScript, Vitest, Biome)
4. Run `pnpm check` to see all validation issues at once

## Useful References

- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [Vitest Documentation](https://vitest.dev/)
- [Biome Documentation](https://biomejs.dev/)
- [pnpm Documentation](https://pnpm.io/)
