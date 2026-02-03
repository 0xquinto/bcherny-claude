Create a new git worktree for running a parallel Claude Code session.

Steps:

1. If no name argument was provided, generate one from today's date and a short descriptor (e.g., `2026-02-03-feature`)
2. Run: `git worktree add .claude/worktrees/$name origin/main`
3. Confirm the worktree was created successfully
4. Print the launch command: `cd .claude/worktrees/$name && claude`
5. Remind the user they can list worktrees with `git worktree list` and remove with `git worktree remove .claude/worktrees/$name`
