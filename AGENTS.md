# Documentation project instructions

## About this project

- The user-facing documentation for [Time2Bike](https://time2.bike), a bike-racing
  platform covering registration, race-day timing, results, teams and merch.
- Built on [Mintlify](https://mintlify.com). Pages are MDX with YAML frontmatter.
- Configuration and navigation live in `docs.json`.
- Run `mint dev` to preview locally.
- Run `mint broken-links` to check links.

Docs are organized by **audience**, not by feature area: `riders/`, `teams/`,
`organizers/`, `timing/`, and `platform/` (cross-cutting reference). Write for
the person named by the directory you're in — an organizer page can assume
someone is running an event; a rider page cannot.

## Terminology

These distinctions are load-bearing. Several of them are things real users mix
up, and the docs are often where that gets settled.

### The three that get confused

| Term | Means |
| --- | --- |
| **Organization** | Hosts events and takes entry fees. Owns the Stripe account. |
| **Team** | A racing club riders belong to. Has a roster, practices, a public page. |
| **League** | A governing body teams race under. Governs eligibility, dues, credentials. |

They are separate, they don't share permissions, and one person can be involved
in all three.

### Event and race

An **event** is the thing on a calendar with a date and a location. A **race**
is one competition inside it — a category, a distance, a start wave. An event
has many races. Never use them interchangeably: "register for the event" and
"register for a race" mean different things at checkout.

A **series** links events into a championship with standings. A **recurring
event** is one event that repeats — a weekly practice crit — with each running
called an **occurrence**.

### Profile and participant

A **profile** is the stored racing identity — name, date of birth, category,
race history — that lives at `/profiles`. One account can hold several:
yourself, your kids, teammates who shared theirs with you. When you mean the
saved record, write "profile".

A **participant** is a person entered in a race. That is the sense used by the
registration wizard's Participants step and by the organizer's Participants tab
(everyone entered in your event). When you mean somebody on a start list, write
"participant".

The distinction is record vs. entry: you *edit a profile*, and you *register a
participant*. Don't call the `/profiles` page a participants list — the product
stopped doing that, because it collided with the organizer tab of that name.

### Bib and plate

A **bib** is the number a rider wears at one event. A **plate** is a number held
for a whole season, assigned by a series or a league. A race's *bib source*
decides which one gets used on the day. Both words appear in the product, so
keep them straight rather than picking one.

### Sign in / sign out

The product says **sign in** and **sign out**. Not "log in", "login", or
"log out".

## Style preferences

- Use active voice and second person ("you").
- Keep sentences concise — one idea per sentence.
- Use sentence case for headings, matching the product UI.
- Bold for UI elements: Click **Settings**. Match the product's own casing —
  if the button says "New profile", write **New profile**, not **New Profile**.
- Code formatting for file names, commands, paths, URLs, and code references.
- Navigate with arrows for multi-step paths: **Event → Bibs**.
- Prefer naming what a thing does over what it is called. A reader searching for
  "how do I stop people entering after Friday" should find the page about price
  schedules.

## Content boundaries

- **Document the product as it ships.** If a screen doesn't exist yet, don't
  describe it. Use a `{/* IMAGE NEEDED: ... */}` comment for a screenshot that
  hasn't been taken rather than describing a placeholder.
- **Don't document the site-admin area** (`/admin`). It is internal to
  Time2Bike staff and is not part of the customer product.
- **Don't publish internal implementation detail** — database shape, API route
  names, or infrastructure. `platform/` is for user-visible cross-cutting
  behaviour (slugs, payouts, permissions, SEO), not architecture.
- **Money and legal wording is deliberate.** Fee percentages, refund behaviour,
  waiver and guardian-consent rules, and age-of-majority handling should match
  the product exactly. If you can't verify a number, leave it out rather than
  approximating it.

## When the UI changes

A page that names a button is a page that goes stale. If you rename something in
the product, grep the docs for the old string before shipping:

```bash
grep -rn "Old Button Name" --include="*.mdx" .
```

Every `.mdx` on disk must appear in `docs.json`, and every `docs.json` entry must
have a file. Both directions are currently clean; keep them that way.
