# Time2Bike documentation

The user-facing documentation for [Time2Bike](https://time2.bike), published
at **[docs.time2.bike](https://docs.time2.bike)**.

Built with [Mintlify](https://mintlify.com). Pages are MDX with YAML
frontmatter; the site structure lives in `docs.json`.

## Layout

The docs are organized by who the reader is, not by how the software is built.
Each top-level directory is a tab in the published site:

| Directory | Tab | Who it's for |
| --- | --- | --- |
| `riders/` | Riders | People entering races: accounts, registration, waivers, results, profiles |
| `teams/` | Teams | Clubs and coaches: rosters, practices, applications, racing together |
| `organizers/` | Organizers | Race directors: organizations, events, races, pricing, merch, imports |
| `timing/` | Live Timing | Race-day operators: the timing screen, formats, hardware, publishing results |
| `platform/` | Reference | Cross-cutting topics: slugs, roles, Stripe Connect, uploads, SEO |

`index.mdx` is the landing page.

## Local development

```bash
npm i -g mint     # once
mint dev          # serves http://localhost:3000
```

Run from the repository root, where `docs.json` lives.

```bash
mint broken-links   # check internal links before opening a PR
```

## Adding a page

1. Create the `.mdx` file in the directory for its audience.
2. Give it frontmatter — `title`, `description`, and an `icon`.
3. Add its path (without the `.mdx`) to the right group in `docs.json`.

A page that isn't listed in `docs.json` won't appear in the navigation. Every
page currently on disk is in the navigation; keep it that way.

## Writing

See `AGENTS.md` for terminology and style — in particular the product
vocabulary, which is deliberate and worth reading before writing a page.
`CONTRIBUTING.md` covers the pull request process.

## Publishing

Merging to the default branch deploys to production via the Mintlify GitHub
app.

## Screenshots

The September 2026 screenshot update uses the real application UI with fictional
demo records. Sample names, addresses, contact details, license numbers, and
join codes are examples; they do not come from customer accounts. Hardware
readings are simulated where the caption says so. Results PDFs come from the
application's PDF renderer with demo results. Older screenshots have also been
replaced in place, and unused legacy images removed.

When replacing a screenshot, use demo data, include descriptive alt text, and
check the final image for personal details, usable access links or QR codes,
floating panels, and clipped controls. Keep the image focused on the task.
Leave an `IMAGE NEEDED` comment when the requested view is unavailable; do not
recreate a screen that the application does not provide.

The expanded result-history screenshot in `timing/history-and-audit.mdx` is
still pending because the current operator screen has no expanded history view.
