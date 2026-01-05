# CLAUDE.md - Project Instructions for Claude Code

This file provides project-specific guidance for Claude Code. Update this file whenever Claude does something incorrectly so it learns not to repeat mistakes.

## Project Overview

Dropshipping/Amazon FBA project. This codebase will contain tools, automations, and applications related to e-commerce operations.

## Development Workflow

1. Make changes
2. Run typecheck (if TypeScript project)
3. Run tests
4. Lint before committing
5. Before creating PR: run full lint and test suite

## Code Style & Conventions

- Prefer `type` over `interface`; avoid `enum` (use string literal unions instead)
- Use descriptive variable names
- Keep functions small and focused
- Write tests for new functionality
- Handle errors explicitly, don't swallow them

## Commands Reference

```sh
# TypeScript/Node projects (once set up)
npm run typecheck        # Type checking
npm run test            # Run tests
npm run lint            # Lint all files
npm run format          # Format code

# Git workflow
git status              # Check current state
git diff                # Review changes before commit
```

## Important Notes

- Always verify changes work before committing
- Run the relevant tests after making changes
- When unsure about project conventions, check existing code for patterns
- Don't introduce new dependencies without good reason

## Things Claude Should NOT Do

- Don't use `any` type in TypeScript without explicit approval
- Don't skip error handling
- Don't commit without running tests first
- Don't make breaking API changes without discussion

## Project-Specific Patterns

(Add patterns specific to this project as they emerge)

---

*Update this file whenever you notice Claude making mistakes or when new conventions are established.*
