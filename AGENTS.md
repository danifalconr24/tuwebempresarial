# Agent Instructions

## Project

- Astro 5 static site; runtime entrypoint is `src/pages/index.astro`.
- Page composition lives in `src/components/`; shared document metadata and global CSS live in `src/layouts/Layout.astro`.
- `presentacion.html` is a standalone client presentation, not part of Astro's page route.
- `public/` contains files served at site root. Astro config sets canonical site URL to `https://tuwebempresarial.com` and enables sitemap generation.

## Commands

- Install locked dependencies: `npm ci`.
- Start local development: `npm run dev`.
- Create production build: `npm run build`.
- Preview production build: `npm run preview`.
- No test, lint, or typecheck scripts are configured; use `npm run build` as current verification.

## Environment

- Copy `.env.example` to `.env` and set `PUBLIC_WEB3FORMS_KEY` before testing the contact form. `src/components/Contact.astro` submits directly to Web3Forms from the browser.
- Keep `.env` and `.env.production` out of version control; they are ignored.

## Deployment

- Manual GitHub Actions deployment: `.github/workflows/deploy.yml` builds the static site and updates `/opt/tuwebempresarial/site` on the VPS, then runs the existing Compose deployment.
- Required GitHub Actions secrets: `PUBLIC_WEB3FORMS_KEY`, `VPS_HOST`, `VPS_USER`, and `VPS_SSH_PRIVATE_KEY`.
- Current VPS deployment serves HTTP on port `8080`; existing services own ports `80` and `443`.

## Changes

- Preserve Spanish user-facing copy and existing responsive layout conventions when editing the landing page.
- Keep generated `dist/` and `.astro/` output uncommitted.
