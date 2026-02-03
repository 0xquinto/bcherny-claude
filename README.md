# Boris Cherny's Claude Code Setup

This repository contains a Claude Code configuration based on [Boris Cherny's X thread](https://x.com/bcherny/status/2007179832300581177) about how he uses Claude Code.

Boris is the creator of Claude Code at Anthropic, and this setup reflects his personal workflow.

## What's Included

### CLAUDE.md

Project-specific instructions that Claude reads on startup. Update this file whenever Claude makes a mistake so it learns not to repeat it.

### Slash Commands (`.claude/commands/`)

| Command           | Description                                             |
| ----------------- | ------------------------------------------------------- |
| `/commit-push-pr` | Commit, push, and open a PR                             |
| `/quick-commit`   | Stage all changes and commit with a descriptive message |
| `/test-and-fix`   | Run tests and fix any failures                          |
| `/review-changes` | Review uncommitted changes and suggest improvements     |
| `/worktree`       | Create a git worktree for parallel Claude sessions      |
| `/grill`          | Adversarial code review — don't ship until it passes    |
| `/techdebt`       | End-of-session sweep for duplicated and dead code       |

### Subagents (`.claude/agents/`)

| Agent             | Purpose                                                      |
| ----------------- | ------------------------------------------------------------ |
| `code-simplifier` | Simplify code after Claude is done working                   |
| `code-architect`  | Design reviews and architectural decisions                   |
| `verify-app`      | Thoroughly test the application works correctly              |
| `build-validator` | Ensure project builds correctly for deployment               |
| `oncall-guide`    | Help diagnose and resolve production issues                  |
| `staff-reviewer`  | Review plans and architectures as a skeptical staff engineer |

### Settings (`.claude/settings.json`)

- **Pre-allowed permissions**: Common safe commands (npm, git, gh, etc.) won't prompt for approval
- **PostToolUse hook**: Auto-formats code after Write/Edit operations

## Tips from the Claude Code Team

Based on [Boris Cherny's thread (Jan 2026)](https://x.com/bcherny/status/2017742741636321619) sharing tips sourced directly from the Claude Code team.

### Parallelism

- Run 3-5 Claude sessions in parallel using git worktrees
- Use subagents to throw more compute at problems
- Offload tasks to subagents to keep your main context clean
- Route permission requests to Opus 4.5 via a hook to auto-approve safe ones

### Planning

- Start complex tasks in plan mode (shift+tab)
- When things go sideways, re-plan instead of pushing through
- Use plan mode for verification steps, not just builds

### Configuration

- Invest in your CLAUDE.md — update it after every mistake
- Create reusable skills and commit them to git
- Use /statusline to show context usage and git branch
- Color-code and name terminal tabs, one per task/worktree

### Prompting

- Challenge Claude: "Grill me on these changes"
- Demand proof: "Prove to me this works"
- Reset mediocre work: "Scrap this, implement the elegant solution"
- Write detailed specs to reduce ambiguity

### Workflow

- Paste Slack bug threads and just say "fix"
- Say "Go fix the failing CI tests" — don't micromanage how
- Point Claude at docker logs to troubleshoot distributed systems
- Use Claude for analytics — works with any database CLI, MCP, or API

### Learning

- Enable "Explanatory" output style in /config to learn the _why_
- Have Claude generate visual HTML presentations for unfamiliar code
- Ask Claude to draw ASCII diagrams of protocols and codebases
- Use voice dictation (fn x2 on macOS) — you speak 3x faster than you type

### Terminal

- The team recommends Ghostty for its synchronized rendering and unicode support

## How to Use This Repo

### Option 1: Copy to Your Project

Copy the `.claude/` folder and `CLAUDE.md` to the root of your existing project:

```sh
cp -r /path/to/bcherny-claude/.claude /path/to/your-project/
cp /path/to/bcherny-claude/CLAUDE.md /path/to/your-project/
```

### Option 2: Use as a Template

Clone this repo and use it as a starting point for a new project:

```sh
git clone <this-repo> my-new-project
cd my-new-project
rm -rf .git
git init
```

### Option 3: Cherry-pick What You Need

Copy only specific files you want:

- Just want slash commands? Copy `.claude/commands/`
- Just want subagents? Copy `.claude/agents/`
- Just want permissions? Copy `.claude/settings.json`

### After Setup

1. **Customize CLAUDE.md** for your project's tech stack, conventions, and workflow
2. **Edit settings.json** to match your project's commands (e.g., `bun` instead of `npm`)
3. **Run Claude Code** in your project directory - it will automatically read the config

### Using the Commands

In Claude Code, type `/` to see available commands:

```
/commit-push-pr     # Full git workflow
/quick-commit       # Fast commit
/test-and-fix       # Run and fix tests
/review-changes     # Code review
/worktree           # Parallel Claude sessions
/grill              # Adversarial code review
/techdebt           # Codebase cleanup
```

### Using Subagents

Ask Claude to use a subagent:

```
"Use the code-simplifier agent to clean up the code I just wrote"
"Run the verify-app agent to test everything works"
"Use code-architect to review this design"
```

## Sources

- Original setup: https://x.com/bcherny/status/2007179832300581177
- Team tips (Jan 2026): https://x.com/bcherny/status/2017742741636321619
