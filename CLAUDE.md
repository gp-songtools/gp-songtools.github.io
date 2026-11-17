# CLAUDE.md

## Project
- Root GitHub Pages site for the `gp-songtools` org: `https://gp-songtools.github.io/`
- Redirects and shared files only; every tool lives in its own repo at `/<repo>/`
- No build step, no dependencies; push to `main` deploys

## Directory map
- `index.html` — root → `/toolsmenu/`
- `suno-style-creator/index.html` — old GP Blueprint address → `/gp-blueprint/`
- `404.html` — forwards moved paths (`MOVED` map), else "not found" with a link to the menu
- `.nojekyll` — serve files as-is (needed for `.well-known/`)
- `README.md`, `CLAUDE.md`

## Rules
- A project repo's path always wins over a folder here; only add folders for names no repo uses
- When a tool's repo is renamed: add its old path to `MOVED` in `404.html` and an `<old>/index.html` redirect
- `404.html` also serves missing pages on tool sites without their own 404: keep it generic
- Redirect pages carry no analytics snippet (they redirect instantly; the target page counts the visit)
- Future: `.well-known/assetlinks.json` for the Android app (Trusted Web Activity) goes here
- Check layout at 390 px; colors via CSS vars with a `prefers-color-scheme: dark` override

# Multi-Agent Delegation Rules
When acting as the primary session (Opus), operate as a **Tech Lead and Architect**. Conserve primary context and rate limits by delegating execution work to specialized subagents whenever possible.
## Available Subagents
1. **`haiku-helper` (Fast Scout & Clerk)**
- **When to delegate:** File discovery, searching across the codebase (`Grep`/`Glob`), checking git status or commit logs, reading configuration files, and summarizing documentation.
- **Constraint:** Read-only tasks. Do not ask `haiku-helper` to write or edit code.
2. **`sonnet-worker` (Builder & Tester)**
- **When to delegate:** Implementing features from a finalized specification, writing unit or integration tests, refactoring isolated modules, fixing localized bugs, and running test/build suites.
- **Constraint:** Always provide clear requirements, target file paths, and expected behavior when invoking `sonnet-worker`.
## Orchestration Workflow
1. **Explore First:** Before planning changes, dispatch `haiku-helper` to locate relevant files and summarize existing patterns.
2. **Design & Plan:** Synthesize the findings in the main session and outline the architectural plan or edge cases.
3. **Delegate Implementation:** Hand off well-scoped coding, refactoring, and test-writing tasks to `sonnet-worker`. You may launch multiple `sonnet-worker` instances in parallel for independent modules.
4. **Review & Verify:** Inspect the changes made by `sonnet-worker` (or have `haiku-helper` summarize `git diff`) to ensure architectural alignment before concluding the task.
