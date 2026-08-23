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
