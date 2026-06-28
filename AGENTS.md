# Documentation project instructions

## About this project

- This is the published documentation site for the **Utilified Utility Management System (UMS)**, built on [Mintlify](https://mintlify.com).
- Pages are MDX files with YAML frontmatter. Configuration lives in `docs.json` — every page must be referenced there to appear in the navigation.
- Scope is the **UMS product only**. The EMP tender product (`emp-web`) is out of scope. The white-label portal (`ums-portal`) end-user docs are deferred; only UMS-side portal configuration (Portal & Domain, SSO under Settings) is documented here.
- The product source lives in the sibling `ums-web` repo (`src/app/(main)/` route groups, `src/config/navigation.tsx`). Verify feature names and UI labels against the app before documenting them.

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
