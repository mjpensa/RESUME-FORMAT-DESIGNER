# CLAUDE.md — RESUME-FORMAT-DESIGNER

## Environment Overview

This is a resume format research project running in Anthropic-hosted Claude Code cloud sessions on Ubuntu Linux. Git operations route through a local proxy on `127.0.0.1:62100` — direct access to `github.com` is not available. The `gh` CLI is not installed and GitHub API tokens are not exposed. All commits are signed automatically via SSH.

## Bootstrap

```bash
# Verify proxy connectivity
git ls-remote origin

# Verify commit signing is configured
git config --get commit.gpgsign
git config --get gpg.format
```

## External Tool Configuration

### GitHub (via Local Proxy)

#### Connection

All git operations route through a **local proxy** — never directly to `github.com`.

- **Remote URL:** `http://local_proxy@127.0.0.1:62100/git/mjpensa/RESUME-FORMAT-DESIGNER`
- The proxy intercepts push, fetch, and pull.
- Direct `github.com` URLs will **not** work.

> **Important:** The `gh` CLI is NOT available in this environment. Use `git` commands only.

#### Authentication

Proxy handles auth transparently. No tokens in git config.

```ini
[http]
    proxyAuthMethod = basic
```

#### Identity & Signing

```ini
[user]
    name = Claude
    email = noreply@anthropic.com
    signingkey = /home/claude/.ssh/commit_signing_key.pub
[gpg]
    format = ssh
[gpg "ssh"]
    program = /tmp/code-sign
[commit]
    gpgsign = true
```

#### Access Policies

- Push only to `claude/*` branches (403 otherwise).
- Auto-merge workflow merges `claude/*` → `main`. See **CI / CD Hooks**.

**Pre-push checklist:**

```bash
git branch --show-current | grep -q "^claude/" && echo "✔ branch OK" || echo "✗ must be claude/*"
git remote get-url origin | grep -q "127.0.0.1:62100" && echo "✔ remote OK" || echo "✗ must use proxy"
```

#### Smoke Test

```bash
git ls-remote origin && echo "✔ proxy OK" || echo "✗ proxy unreachable"
git log --show-signature -1 2>/dev/null | grep -q "Good" && echo "✔ signing OK" || echo "⚠ not verified yet"
```

#### Troubleshooting

| Symptom | Cause | Fix |
|---|---|---|
| `403` on push | Wrong branch | Use `claude/<session-id>` |
| `403` on push | Pushing to `main` | Use `claude/*`; auto-merge handles `main` |
| `repository not found` | Wrong proxy URL | Check `git remote get-url origin` |
| `gh: command not found` | Not in cloud env | Use `git` only — `gh` is not available here |
| Unsigned commit | Missing key/program | Verify `/home/claude/.ssh/commit_signing_key.pub` and `/tmp/code-sign` exist |

## CI / CD Hooks

### Auto-Merge Workflow

File: `.github/workflows/auto-merge-claude.yml`

This workflow runs in **GitHub Actions** (not in this cloud environment). On every push to a `claude/**` branch, it automatically merges that branch into `main`.

- **Trigger:** `push` to `claude/**`
- **Action:** Checks out `main`, merges the `claude/*` branch, pushes `main`
- **Actor:** `github-actions[bot]`

You do not need to merge manually. Push to your `claude/*` branch and the workflow handles propagation to `main`.

## Troubleshooting

| Symptom | Cause | Fix |
|---|---|---|
| Network timeout on git operations | Proxy not running | Wait and retry; proxy starts automatically |
| Cannot install packages via `brew` | Not available in cloud | Use `apt` or `pip` if needed |
| `Permission denied` on signing key | Key path incorrect | Verify `/home/claude/.ssh/commit_signing_key.pub` exists |
| Push succeeds but `main` not updated | Workflow not triggered | Confirm branch matches `claude/**` pattern |
