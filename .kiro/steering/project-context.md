# Velvosoft Project — Context for Kiro

This file gives Kiro the background it needs to work in this project without re-explaining.

## What this project is

This is a **static snapshot / backup copy** of the live website
[velvosoft.biz](https://velvosoft.biz/), the site for **Velvosoft**, a Bangalore-based
hygiene product manufacturer (tissue products and hygiene cleaning solutions).

The owner is **Md Touseef** (GitHub: `mdtouseef15`).

## How the live site is built

- **Platform:** WordPress with the **Elementor** page builder
- **Hosting:** LiteSpeed / PHP, host `mysecurecloudhost.com`
- **Domain registrar:** GoDaddy
- Live page content and designs live in a **MySQL database**, not in editable code files.
  Nobody hand-wrote the HTML — Elementor generates it.

## Repository structure

| Path | Description |
|------|-------------|
| `snapshot/` | Self-contained static mirror of the public site (HTML/CSS/JS/images/fonts). Renders standalone. |
| `README.md` | Project overview. |
| `HOW-TO-UPDATE.md` | Step-by-step guide for refreshing the GitHub copy after website changes. |

## GitHub

- Remote: **https://github.com/mdtouseef15/velvosoft-website** (public)
- Branch: `main`, tracking `origin/main`
- Commit identity: name `Md Touseef`, email `mdtouseef15@users.noreply.github.com`
- Auth: GitHub CLI (`gh`) over HTTPS

## Critical facts (do not forget)

1. **Editing this folder does NOT change the live website.** The live site is served from
   WordPress + a database on the host. To change what visitors see, the owner edits in
   **WordPress/Elementor** at `velvosoft.biz/wp-admin`, not here.

2. **Nothing syncs automatically.** GitHub only updates when someone runs
   `git add -A && git commit && git push`. The live site → GitHub has no automatic link either.

3. **To refresh the snapshot after the live site changes**, re-run the `wget` mirror
   (see `HOW-TO-UPDATE.md`), then commit and push.

4. **Never commit secrets.** `.gitignore` excludes `wp-config.php`, `.env`, and `*.sql`.
   If a full WordPress backup (files + database) is ever added, keep it in a **private** repo.

## Known content issue to flag

The live site has a leftover "Why Velvosoft Stands Out" section mentioning
"custom software and automations" — this is template boilerplate that does not match a
hygiene/tissue brand. The owner may want to rewrite it in Elementor.

## How the owner wants to work

- The owner does **not** want to hand-code; edits to the live site happen visually in Elementor.
- Kiro's role: advise on content/copy, maintain the snapshot/backup, and handle all Git
  commits and pushes. When the owner says "update GitHub," re-snapshot and push.
