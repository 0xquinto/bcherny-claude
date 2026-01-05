# Boris Cherny's Claude Code Setup

This repository contains a Claude Code configuration based on [Boris Cherny's X thread](https://x.com/bcherny/status/2007179832300581177) about how he uses Claude Code.

Boris is the creator of Claude Code at Anthropic, and this setup reflects his personal workflow.

## What's Included

### CLAUDE.md
Project-specific instructions that Claude reads on startup. Update this file whenever Claude makes a mistake so it learns not to repeat it.

### Slash Commands (`.claude/commands/`)
| Command | Description |
|---------|-------------|
| `/commit-push-pr` | Commit, push, and open a PR |
| `/quick-commit` | Stage all changes and commit with a descriptive message |
| `/test-and-fix` | Run tests and fix any failures |
| `/review-changes` | Review uncommitted changes and suggest improvements |
| `/first-principles` | Deconstruct problems to fundamental truths |

### Subagents (`.claude/agents/`)
| Agent | Purpose |
|-------|---------|
| `code-simplifier` | Simplify code after Claude is done working |
| `code-architect` | Design reviews and architectural decisions |
| `verify-app` | Thoroughly test the application works correctly |
| `build-validator` | Ensure project builds correctly for deployment |
| `oncall-guide` | Help diagnose and resolve production issues |

### Settings (`.claude/settings.json`)
- **Pre-allowed permissions**: Common safe commands (npm, git, gh, etc.) won't prompt for approval
- **PostToolUse hook**: Auto-formats code after Write/Edit operations

## Key Tips from Boris

1. **Run multiple Claudes in parallel** - Number terminal tabs 1-5, use system notifications
2. **Use Opus 4.5 with thinking** - Best coding model, better at tool use
3. **Start sessions in Plan mode** (shift+tab twice) - Iterate on plan, then auto-accept
4. **Give Claude verification loops** - Tests, typecheck, lint = 2-3x quality improvement
5. **Update CLAUDE.md continuously** - Tag @claude in PR reviews to add learnings
6. **Use slash commands** for repetitive "inner loop" workflows

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
/first-principles   # Problem analysis
```

### Using Subagents

Ask Claude to use a subagent:
```
"Use the code-simplifier agent to clean up the code I just wrote"
"Run the verify-app agent to test everything works"
"Use code-architect to review this design"
```

## Source

Based on: https://x.com/bcherny/status/2007179832300581177
