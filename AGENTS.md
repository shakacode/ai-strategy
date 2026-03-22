# AGENTS.md

Instructions for AI coding agents working on the `ai.shakacode.com` repository.

This repository is an Astro static site for ShakaCode AI strategy content.

## Canonical Agent Policy

`AGENTS.md` is the canonical source for repository-wide agent rules:

- Commands and local verification workflow
- Code style and formatting expectations
- Git/PR safety boundaries
- Review-comment handling workflow

If there is a conflict with other agent-facing docs, `AGENTS.md` wins.

## Commands

```bash
# Install dependencies
npm install

# Local development
npm run dev

# Production build (required verification before merge)
npm run build

# Preview production build
npm run preview
```

## Project Structure

| Directory / File         | Purpose                                               |
| ------------------------ | ----------------------------------------------------- |
| `src/pages/`             | Site pages (`.astro` and article `.md` files)        |
| `src/layouts/`           | Shared page layouts                                   |
| `src/styles/global.css`  | Global styles                                         |
| `.claude/commands/`      | Claude command definitions                            |
| `.claude/commands/address-review.md` | Review-comment handling command             |

## Review Workflow

When asked to address PR review comments:

1. Gather actionable comments from the PR (ignore bot noise and replies).
2. Apply fixes in focused commits.
3. Reply to the original PR comments/threads with what changed.
4. Verify with `npm run build`.

For Claude users, use `.claude/commands/address-review.md`.

## Code Style

- Keep content edits intentional and scannable.
- Reuse existing design patterns in this site unless explicitly redesigning.
- Prefer CSS variables over hardcoded colors for reusable UI styles.
- Ensure all files end with a newline.

## Git Workflow

- One logical change per commit.
- Keep PR descriptions clear: summary, why, scope, validation.
- Before merge, ensure `npm run build` passes locally.

## Boundaries

### Always

- Run `npm run build` before claiming a change is complete.
- Reply to review comments after addressing them.
- Keep links and repository references up to date.

### Ask First

- Destructive git operations (force push, reset, branch deletion)
- Workflow changes under `.github/workflows/`

### Never

- Commit secrets or credentials
- Skip verification and claim completion
