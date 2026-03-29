# OpenClaw Migration Scripts

These are sanitized companion scripts for the article:

- [`../index.md`](../index.md)

They are intentionally generic. Replace the placeholder hostnames, usernames, and email addresses with your own values before running them in production.

The article keeps both SVG and Mermaid diagrams on purpose. The SVGs are ready for publishing, and the Mermaid blocks stay editable in Git.

## Recommended order

1. Run [`01-quick-start-agent-box-admin.sh`](01-quick-start-agent-box-admin.sh) on the destination Mac as the admin user.
2. Run [`02-quick-start-main-machine.sh`](02-quick-start-main-machine.sh) on your main Mac.
3. Log into the destination Mac's `agents` user once locally, then run [`03-quick-start-agents-user.sh`](03-quick-start-agents-user.sh).
4. Run [`04-bootstrap-agent-github.sh`](04-bootstrap-agent-github.sh) as the destination `agents` user.
5. Copy OpenClaw state using either:
   - [`05-migrate-openclaw-state-direct.sh`](05-migrate-openclaw-state-direct.sh), or
   - [`06-bridge-openclaw-state.sh`](06-bridge-openclaw-state.sh)
6. Run [`07-rewrite-openclaw-paths-for-macos.sh`](07-rewrite-openclaw-paths-for-macos.sh) on the destination Mac.
7. Run [`08-verify-openclaw-migration.sh`](08-verify-openclaw-migration.sh) on the destination Mac.
8. Before decommissioning the source, run [`09-backup-openclaw-from-source.sh`](09-backup-openclaw-from-source.sh) on the main Mac.

## Important

- Do not copy `~/.config/gh/` from the source machine.
- Do not copy the source machine's SSH private key unless you explicitly want the same key material on two machines.
- Do not publish real copies of `openclaw.json`, `credentials/`, `identity/`, or `.env.*`.
