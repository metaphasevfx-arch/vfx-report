# VFX Dashboard - Separate GitHub Pages Site

This folder is prepared as a standalone static website deployment.
It is isolated from the main `clapkit.pro` site.

## Current domain setup

- Main website (already existing): `clapkit.pro`
- This dashboard (new, separate site): `vfx-dashboard.clapkit.pro`

If you want another subdomain, change only the value in `CNAME`.

## What is already prepared

- `index.html`, `assets/`, `photos/`, `data/` copied from your dashboard export
- `CNAME` with `vfx-dashboard.clapkit.pro`
- `.nojekyll` to ensure static files are served as-is
- GitHub Actions workflow: `.github/workflows/deploy-pages.yml`

## 1. Create a new GitHub repository

Create a new repo, for example: `vfx-dashboard-pages`.

Important: do not reuse the existing `ClapKit_web` repository.

## 2. Push this folder to the new repository

Run from this directory:

```bash
cd "/Users/feodorlebedev/Documents/Codex/2026-05-19/users-feodorlebedev-downloads-vfx-dashboard-20260516/vfx-dashboard-pages"
git init
git add .
git commit -m "Initial VFX dashboard pages site"
git branch -M main
git remote add origin https://github.com/metaphasevfx-arch/vfx-dashboard-pages.git
git push -u origin main
```

If repository name/owner differs, replace the remote URL.

## 3. Enable GitHub Pages in repository settings

On GitHub:

1. Open repo `Settings` -> `Pages`
2. In `Build and deployment`, set `Source: GitHub Actions`
3. Wait for workflow `Deploy VFX Dashboard to GitHub Pages` to finish

## 4. DNS in Namecheap (or your DNS provider)

Add a single record:

- Type: `CNAME`
- Host: `vfx-dashboard`
- Value: `metaphasevfx-arch.github.io`
- TTL: Automatic

Do not change existing apex `A` records for `clapkit.pro`.
Those belong to your main website and must stay as-is.

## 5. Connect custom domain in GitHub Pages

In `Settings` -> `Pages` of the new repository:

- Set `Custom domain`: `vfx-dashboard.clapkit.pro`
- Enable `Enforce HTTPS` after DNS is propagated

## Result

You will have a separate shareable link:

- `https://vfx-dashboard.clapkit.pro`

Main site remains untouched:

- `https://clapkit.pro`
