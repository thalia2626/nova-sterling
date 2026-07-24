# CLAUDE.md — nova-sterling

Guidance for Claude Code when working in this repo.

## Project

Static HTML site for **Nova Sterling**, a modern lifestyle brand / creative-partner
model site (black / white / gold editorial styling). Plain HTML + inline CSS, no build
step, no dependencies.

Key files (repo root):
- `index.html` — **the live homepage** (Nova Sterling editorial site).
- `index-thalia.html` — older "Thalia Model Portfolio" site (dark + tan). Preserved, not the homepage.
- `nova.html`, `nova-editorial.html` — additional Nova Sterling pages.
- `backups/`, `thalia-old/` — prior versions kept for reference.
- `images/` — image assets.

## Live site (GitHub Pages)

- URL: **https://thalia2626.github.io/nova-sterling/**
- Source: branch `main`, folder `/` (root). Serves `index.html`.
- **Auto-deploys on every push** to `main` — usually live within ~1 minute. No extra step.

## Environment

- Windows 11, PowerShell (Windows PowerShell 5.1). See PowerShell quirks: no `&&`/`||`
  chaining, use `;` and `if ($?)`.
- Git installed at `C:\Program Files\Git\cmd\git.exe` (on PATH for new terminals; if a
  shell can't find it, prepend `$env:Path = "C:\Program Files\Git\cmd;" + $env:Path`).
- GitHub CLI (`gh`) installed at `C:\Program Files\GitHub CLI\gh.exe`.

## Git workflow — authentication is SSH

Remote is `git@github.com:thalia2626/nova-sterling.git` (SSH, no passwords/prompts).
An ed25519 key is set up locally and registered on the GitHub account.

To publish changes:

```powershell
cd C:\Users\ktakl\Thalia
git add -A
git commit -m "describe the change"
git push          # SSH — no prompt; triggers a Pages redeploy
git pull          # to fetch changes made on github.com
```

## Repo settings (Pages config, About URL, etc.)

SSH only moves code — it **cannot** change repository settings. Those go through the
GitHub API via `gh`, which needs a token (`gh` is not persistently authenticated here).
When settings work is needed, ask the user to create a short-lived, repo-scoped
fine-grained Personal Access Token (permissions: **Pages** + **Administration**,
read/write), use it via `$env:GH_TOKEN` for the `gh` calls, then have the user delete it.
**Never store a token in this repo or any file.** The repo is public.

## Preferences

- **Free tools only** — the user never pays. Default to free tiers / open source
  (git, SSH, GitHub Pages, gh CLI). No paid services.
- This repo is **public** — never commit secrets, tokens, or private keys.
