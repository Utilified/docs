# Utilified Documentation

The published documentation site for the **Utilified Utility Management System (UMS)** — the customer-facing product docs at [docs.utilified.com](https://docs.utilified.com). Built with [Mintlify](https://mintlify.com).

This repo is the `platform-docs` submodule of the [Utilified/utilified](https://github.com/Utilified) monorepo. It documents the **UMS** product only (the EMP tender product and the white-label portal are out of scope here).

## Structure

| Path | Contents |
| --- | --- |
| `docs.json` | Site config — navigation, theme, navbar/footer. Every page must be referenced here to appear in the sidebar. |
| `index.mdx`, `home.mdx` | Landing and dashboard pages. |
| `getting-started/` | Onboarding: quick start, logging in, navigating UMS, first steps, key concepts. |
| `guides/` | Task-oriented how-to walkthroughs (use `<Steps>`). |
| `*.mdx` (root) | Per-module reference pages (accounts, invoices, validation, reports, …). |
| `changelog/` | `latest.mdx` and `archive.mdx` release notes (use `<Update>` blocks). |
| `images/<topic>/` | Screenshots, one folder per topic. Reference as `/images/<topic>/<name>.png`. |
| `AGENTS.md` | Instructions for AI agents editing this site (terminology, style, boundaries). |

## Local preview

```bash
npm i -g mint     # Mintlify CLI
mint dev          # serve at http://localhost:3000
mint broken-links # validate internal links before pushing
```

## Conventions

- **Australian English** throughout — "Organisation", not "Organization". See `AGENTS.md`.
- **Bold** for UI elements the user clicks (Click **Settings**); code formatting for paths, fields, and identifiers.
- Wrap screenshots in `<Frame>` and store them under `images/<topic>/`.
- Add every new page to the relevant group in `docs.json`, or it won't render in the nav.
