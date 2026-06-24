# flanboyant.com

> **The talent partner for your core founding team.**  
> Founder-to-founder. No overhead. Direct cap-table alignment.

---

## Project Overview

`flanboyant.com` is a strict single-page, zero-scroll marketing site for a premium, founder-led talent venture operating in San Francisco. The design philosophy is rooted in high-end **Swiss print editorial** aesthetics — no component libraries, no frameworks, no rounded corners.

The site is intentionally a single `index.html` file: lean, fast, and deployable anywhere.

---

## File Structure

```
flanboyant.com/
├── index.html              ← Single-page application (source of truth)
├── README.md               ← This file: project overview & setup
├── BRAND_SYSTEM.md         ← Brand System Design (visual source of truth)
├── CHANGELOG.md            ← Log of all brand & visual changes
└── foundantional/          ← Original template reference (do not modify)
    └── gemini-code-*.html
```

---

## Local Development

No build step required. Serve with any static HTTP server:

```bash
# Python (built-in)
python3 -m http.server 8080

# Node (if installed)
npx -y serve . -p 8080
```

Then open: `http://localhost:8080`

---

## Visual Governance

All visual changes to this site are governed by the **Brand System Design** documented in [`BRAND_SYSTEM.md`](./BRAND_SYSTEM.md).

### Rules
1. **Before any visual change**, consult `BRAND_SYSTEM.md` to verify compliance.
2. **If a change is compatible** with the system → implement and log in `CHANGELOG.md`.
3. **If a change conflicts** with the system → a decision must be made:
   - Does the new change override the system? → Update `BRAND_SYSTEM.md` first, then implement.
   - Does the system override the change? → Do not implement.
4. **Snapshots** of each major brand version are logged in `BRAND_SYSTEM.md` under `## Snapshot History`.

### When to Update the Brand System
- Logo mark or wordmark changes
- Color palette modifications
- Typeface or weight changes
- Spacing grid changes
- New component patterns introduced
- Removal of existing components

---

## Business Parameters (Locked)

These are non-negotiable constraints reflected in the site copy:

| Parameter | Value |
|---|---|
| Location | In-Person · San Francisco |
| Base Salary Floor | $150K |
| Contingency Fee | 20%–25% |
| Contact | WhatsApp |

---

## SEO

- Title: `flanboyant — founding teams`
- Description: `flanboyant is the premier founder-to-founder talent partner for elite seed and Series A startups.`
- OG & Twitter Cards: configured
- Canonical: `https://flanboyant.com`
- Robots: `index, follow`

---

## Deployment

The site is a static HTML file. For a complete production checklist, domain setup, and detailed platform guides, see the dedicated [**Production Deployment Guide (`DEPLOYMENT.md`)**](./DEPLOYMENT.md).

Quick options to deploy to any static host:
- **Vercel**: drag-and-drop or connect Git repo
- **Netlify**: drop the folder
- **Firebase Hosting**: `firebase deploy`
- **GitHub Pages**: push to `gh-pages` branch

---

## Git Versioning & Deployment Best Practices

To maintain the high-quality editorial aesthetic, codebase performance, and clean version history, adhere to the following best practices on GitHub:

### 1. GitHub Versioning & Git Workflow

- **Branch Protection:** 
  - Once the site is in production, avoid pushing experimental or unvetted changes directly to `main`.
  - Use feature/fix branches (e.g., `feature/contact-form`, `fix/typo-terms`) and merge via **Pull Requests (PRs)** after testing.
- **Conventional Commits:** 
  - Keep commits precise, clear, and conventional to allow easy backtracking.
  - Examples:
    - `feat: add dual-audience mode switch and candidate copy`
    - `fix: correct alignment on right panels under 420px container query`
    - `docs: write production deployment guides and dns guidelines`
- **Semantic Versioning (SemVer):**
  - Continue using the `MAJOR.MINOR.PATCH` versioning format for brand snapshots inside `BRAND_SYSTEM.md` and release tags on GitHub.
  - Increment the *Minor* version for new visual patterns (like adding the Mode Switch in `v1.4.0`) and *Patch* for simple copy adjustments or styling fixes.
- **Visual Logs (`CHANGELOG.md`):**
  - Always log any change inside `CHANGELOG.md` using the established category tags: `[BRAND]`, `[LAYOUT]`, `[CONTENT]`, `[SEO]`, or `[FIX]`.

### 2. Performance & Deployment Optimization

- **Continuous Deployment (CI/CD):**
  - Link your GitHub repository directly to Vercel or Cloudflare Pages.
  - This automates production deployment on every commit pushed to `main` and generates **automatic staging/preview URLs** for your pull requests. This lets you inspect visual changes live before merging.
- **Zero-Build/No-Dependency Integrity:**
  - The project is intentionally designed with zero dependencies, build pipelines, or bundling setups to achieve sub-second page loads.
  - Avoid introducing heavy npm packages, Webpack configurations, or third-party JS frameworks unless absolutely requested. Keep the code pure vanilla HTML and CSS.
- **Asset Optimization:**
  - Before uploading new visual assets (like `og-image.png` or icons), compress them using modern tools (such as TinyPNG or squoosh.app) to keep file sizes under 150KB and preserve extreme load speeds.

---

*Last brand snapshot: 2026-06-24. See [`BRAND_SYSTEM.md`](./BRAND_SYSTEM.md) for full design documentation.*
