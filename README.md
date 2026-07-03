# The Platform Collective

Landing site for **The Platform Collective** — a private network of senior, ex-platform operators (Meta, TikTok, Snap, Google and the agencies that scaled on them). Companies get access to the network for one-off, scoped projects. No agency, no retainer.

**Live:** https://theplatformcollective.vercel.app

## Pages

| File | URL | Purpose |
| --- | --- | --- |
| `index.html` | `/` | Landing page: hero, how it works, disciplines, operators, comparison, CTA |
| `access.html` | `/access.html` | Company "Get access" request form |
| `join.html` | `/join.html` | Operator "Join the network" application form |

Plain static HTML/CSS — no build step, no dependencies. Fonts (Playfair Display + Inter) load from Google Fonts.

## Forms

Both forms POST to a single **Google Apps Script** web app, which routes on a hidden `type` field:

- `type=client` (Get access) → appends to a **Clients** tab and **emails** the owner.
- `type=operator` (Join) → appends to the operators tab.

Submissions use a hidden-iframe POST so the page never navigates away; the confirmation state shows once the request is sent. The Apps Script source and setup steps live in the Sheet's Apps Script editor (not in this repo).

To point the forms at a different backend, change the `ENDPOINT` constant near the bottom of `access.html` and `join.html`.

## Deploy

Hosted on **Vercel**, connected to this GitHub repo. Every push to `main` auto-deploys. Framework preset: **Other**; no build command or output directory (static root).

## `design/`

Original design handoff bundle from [Claude Design](https://claude.ai/design) — the HTML/CSS/JS prototypes and the chat transcripts the site was built from. Kept for reference; not served.
