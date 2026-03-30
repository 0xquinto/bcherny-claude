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

- Prefer `type` over `interface`; never use `enum` (use string literal unions instead)
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

## Self-Improvement

After every correction or mistake, update this CLAUDE.md with a rule to prevent repeating it. Claude is good at writing rules for itself.

End corrections with: "Now update CLAUDE.md so you don't make that mistake again."

Keep iterating until the mistake rate measurably drops.

## Working with Plan Mode

- Start every complex task in plan mode (shift+tab to cycle)
- Pour energy into the plan so Claude can 1-shot the implementation
- When something goes sideways, switch back to plan mode and re-plan. Don't keep pushing.
- Use plan mode for verification steps too, not just for the build

## Parallel Work

- For tasks that need more compute, use subagents to work in parallel
- Offload individual tasks to subagents to keep the main context window clean and focused
- When working in parallel, only one agent should edit a given file at a time
- For fully parallel workstreams, use git worktrees:
  `git worktree add .claude/worktrees/<name> origin/main`

## Automation

- Use `/loop` to run a skill on a recurring interval (e.g., `/loop 5m /babysit`)
- Use `/schedule` to schedule Claude to run on a cron-based schedule, up to a week
- Turn repetitive workflows into skills, then loop them for hands-free automation

## Session Management

- Use `/branch` to fork a session, or `claude --resume <session-id> --fork-session` from CLI
- Use `/btw` for side queries without interrupting the agent's current work
- Use `/teleport` to continue a cloud session on your local machine
- Use `/remote-control` to control a local session from your phone or browser
- Use `/voice` (CLI) or the voice button (Desktop) for voice input

## Multi-Repo Work

- Use `--add-dir` (or `/add-dir`) to give Claude access to additional repositories
- Add `"additionalDirectories"` to settings.json to always load extra folders on startup

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
