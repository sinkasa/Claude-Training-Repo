---
description: Publish the site to GitHub - sets up README, GitHub Actions/Pages, scans for secrets, and pushes
---

Run through this checklist for the static site in this repo:

1. **Secret/confidential scan** - Before doing anything else, search the working
   tree (especially `index.html` and any workflow files) for things that should
   never be committed: API keys, access tokens, passwords, private email
   addresses not meant to be public, internal URLs, `.env` files, credentials,
   etc. The only email address that is expected/allowed in `index.html` is the
   FormSubmit lead-delivery address documented in `CLAUDE.md`. If anything
   confidential is found, stop and report it instead of pushing.

2. **README** - Ensure `README.md` exists at the repo root and accurately
   describes the project (purpose, tech stack, structure, page sections, how to
   preview/deploy). Update it if it's missing or out of date with the current
   `index.html`/CLAUDE.md.

3. **GitHub Actions / Pages workflow** - Ensure `.github/workflows/deploy.yml`
   (or equivalent) exists and deploys `index.html` to GitHub Pages on push to
   `main` using `actions/configure-pages`, `actions/upload-pages-artifact`, and
   `actions/deploy-pages`. Create it if missing.

4. **GitHub Pages enabled** - Note for the user that GitHub Pages must have its
   source set to "GitHub Actions" in the repo settings
   (Settings -> Pages -> Build and deployment -> Source). This cannot be done
   via git push and requires the user (or `gh api`) to configure it once.

5. **Git hygiene** - Make sure `.gitignore` excludes OS/editor cruft (e.g.
   `.DS_Store`). Check `git status` for untracked/modified files and confirm
   with the user what should be staged.

6. **Commit and push** - Stage the relevant files, create a commit with a clear
   message describing what changed, and push to `origin main`. Confirm with the
   user before pushing if there are local commits not yet on the remote.

After pushing, summarize what was changed and remind the user to verify the
GitHub Pages source setting and check the Actions tab for the deployment run.
