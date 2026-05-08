# Radius Marketing Design

This repository is a **design and authoring kit for marketing pages on the Radius platform**. It is built around **Cursor agent skills**: structured instructions so AI-assisted development stays on-brand when you ship landing pages, product sites, and ecosystem pages for [Radius](https://radiustech.xyz) (high-throughput stablecoin infrastructure, micropayments, and related products).

The skills encode **when** to use the Radius look, **which** tokens and typography to apply, and **how** to compose layouts—from the main marketing aesthetic to **subdomain and product pages** (for example facilitator, docs, or other `*.radiustech.xyz` experiences).

## What you get

**1. Agent skills (primary deliverable)**  
Markdown skills with YAML front matter, meant to be registered in Cursor (or similar workflows) so agents consistently build **Radius marketing UI**:

- **[`SKILL.md`](SKILL.md)** (`radius-ui-kit`) — Core Radius brand for web: light-mode palette, coral accent, Mona Sans display type, spacing, cards, navigation patterns, and guidance for dashboards, landings, and crypto/fintech surfaces aligned with radiustech.xyz.
- **[`SKILL-subdomain.md`](SKILL-subdomain.md)** (`radius-subdomain-page`) — Layer on top of the base kit for **product and subdomain marketing pages**: nav lockup (Radius → product), hero eyebrows, docs-style grids, code blocks, endpoint pills, and numbered protocol flows—so ecosystem pages still read as “part of Radius.”

Together they are the **source of truth** for tokens, layout patterns, and copy-adjacent structure when generating or refactoring marketing pages for the platform.

**2. Brand and type assets**  
Files the skills assume or reference when implementing pages:

| Path | Role |
|------|------|
| [`Logo/`](Logo/) | Official Radius wordmarks and icons (SVG and PNG; dark and light backgrounds). |
| [`MonaSans-2.0.8/`](MonaSans-2.0.8/) | [Mona Sans](https://github.com/github/mona-sans) family for local builds and `@font-face` usage. See `MonaSans-2.0.8/LICENSE` for font terms. |


## Using the skills in Cursor

Copy or symlink `SKILL.md` and `SKILL-subdomain.md` into your Cursor skills configuration (or project rules) so tasks like “build a Radius landing page” or “match facilitator marketing style” load the right constraints. The front matter in each file describes **name**, **description**, and **when** the skill should apply.

## Preview the reference HTML

Some browsers limit custom fonts over `file://`. From the repository root:

```bash
python3 -m http.server 8080
```

Open `http://localhost:8080/facilitator-radius-style.html`.

## Brand snapshot (marketing default)

- **Mode:** light, warm off-white page background (`#F8F9FB`).
- **Accent:** coral (`#EB6359`) for CTAs and emphasis.
- **Type:** Mona Sans (including expanded widths for display headlines), as documented in the skills and demonstrated in the reference HTML.

For full token lists and component behavior, rely on **`SKILL.md`** and **`SKILL-subdomain.md`**.

## Repository

https://github.com/dtetrault/Radius-Marketing-Design
