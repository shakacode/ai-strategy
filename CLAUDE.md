# CLAUDE.md

Tool-specific guidance for Claude Code in this repository.

## Source of Truth

`AGENTS.md` is the canonical policy for:

- Commands and verification workflow
- Formatting and style expectations
- Git/PR boundaries
- Review-comment handling process

If this file conflicts with `AGENTS.md`, follow `AGENTS.md`.

## Behavioral Defaults

- When confident in a change, commit and push without waiting for extra confirmation.
- Keep PR comments and replies concise and specific.

## Claude-Specific Workflow

Use these command docs:

- `.claude/commands/address-review.md` for fetching and handling PR review comments.

Typical sequence:

1. Run the address-review workflow for the target PR.
2. Apply selected fixes.
3. Reply to the original review comments.
4. Run `npm run build`.
