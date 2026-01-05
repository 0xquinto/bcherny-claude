# CLAUDE.md - Project Instructions for Claude Code

This file provides project-specific guidance for Claude Code. Update this file whenever Claude does something incorrectly so it learns not to repeat mistakes.

## Project Overview

<!-- Customize this section for your project -->

(Describe your project here)

## Development Workflow

Give Claude verification loops for 2-3x quality improvement:

1. Make changes
2. Run typecheck
3. Run tests
4. Lint before committing
5. Before creating PR: run full lint and test suite

## Code Style & Conventions

<!-- Customize these for your project's conventions -->

- Prefer `type` over `interface`; avoid `enum` (use string literal unions instead)
- Use descriptive variable names
- Keep functions small and focused
- Write tests for new functionality
- Handle errors explicitly, don't swallow them

## Commands Reference

```sh
# Verification loop commands (customize for your project)
npm run typecheck        # Type checking
npm run test            # Run tests
npm run lint            # Lint all files
npm run format          # Format code

# Git workflow
git status              # Check current state
git diff                # Review changes before commit
```

## Things Claude Should NOT Do

<!-- Add mistakes Claude makes so it learns -->

- Don't use `any` type in TypeScript without explicit approval
- Don't skip error handling
- Don't commit without running tests first
- Don't make breaking API changes without discussion

## Project-Specific Patterns

<!-- Add patterns as they emerge from your codebase -->

---

_Update this file continuously. Every mistake Claude makes is a learning opportunity._
