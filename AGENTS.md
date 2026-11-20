# Documentation project instructions

## About this project

- This is the published documentation site for the **Utilified Utility Management System (UMS)**, built on [Mintlify](https://mintlify.com).
- Pages are MDX files with YAML frontmatter. Configuration lives in `docs.json` — every page must be referenced there to appear in the navigation.
- Scope is the **UMS product only**. The EMP tender product (`emp-web`) is out of scope. The white-label portal (`ums-portal`) end-user docs are deferred; only UMS-side portal configuration (Portal & Domain, SSO under Settings) is documented here.
- The product source lives in `ums-web/` in the `Utilified/utilified-platform` monorepo, which checks this repo out as its `platform-docs` submodule (`src/app/(main)/` route groups, `src/config/navigationRegistry.tsx`). Verify feature names and UI labels against the app before documenting them.

## Terminology

- Use **Australian English**: "Organisation" (never "Organization"), "Optimise", "Centre". The product UI uses AU spelling — match it.
- **UMS** — Utility Management System (the product). **UtiliRead** — the OCR/vision invoice extraction feature (note the capital R).
- **NMI** — National Meter Identifier (electricity). **MIRN** — Meter Installation Reference Number (gas). **ABN/ACN** — Australian Business/Company Number.
- Entity vocabulary (do not invent synonyms): **Account** (business entity) → **Site** (physical location) → **Connection** (meter point) → **Meter → Register → Reads**. **Agreement** (energy contract), **Retail Account** (retailer's account reference), **Tariff** (rate structure), **Invoice**, **Brokerage**.
- "Connection" ≠ "Site" ≠ "Account" — keep the hierarchy precise. See `getting-started/key-concepts.mdx`.

## Style preferences

- Use active voice and second person ("you").
- Keep sentences concise — one idea per sentence.
- Use sentence case for headings.
- Bold for UI elements: Click **Settings**.
- Code formatting for file names, commands, paths, field names, and identifiers (NMI, ABN).
- Use `<Steps>` for sequential walkthroughs, `<Frame>` to wrap screenshots, `<Note>/<Tip>/<Warning>/<Info>` for asides, `<Tabs>` to mirror tabbed UIs, `<Update>` for changelog entries.

## Content boundaries

- Document **user-facing UMS features** only. Do not document internal admin tooling, backend implementation, Celery queues, API internals, or developer setup.
- Permission/feature-flag-gated modules (e.g. ESG): document them, but state plainly that the section only appears when enabled for the organisation.
- Don't document EMP. Defer white-label portal end-user workflows; do cover the UMS-side configuration an operator performs.
- Verify against `ums-web` source before stating column names, field labels, or workflow steps — don't guess.

## Structure

- The `docs.json` navigation mirrors the app sidebar's groups: Home and inbox, Portfolio, Operations, Commercial, Billing, Insights, then Settings and tools. Put a page in the group where its screen lives in the app. Guides go in that group's guides sub-group.
- Removing or renaming a page needs an entry in `docs.json` `redirects`, and every inbound link updated. `mint broken-links` must pass.
- Module pages follow this order: where to find it (sidebar group › item › tab), what it's for, tabs and views (a table), actions, statuses, related guides.
- Every module page and guide lists the app routes it documents in frontmatter, for example `ums_routes: ["/connections", "/connections/[id]"]`. Mintlify ignores the key. Drift checks use it to find the page to update when those routes change.
- Name buttons by their label, such as **New Connection**. Don't write "+".

## Screenshots

- Capture screenshots only from the local seeded stack (`dev:local` with demo data), never from production. Production holds customer data.
- When the UI a screenshot shows has changed and you can't recapture it, add `{/* screenshot-stale */}` above its `<Frame>` rather than leaving it unmarked.
