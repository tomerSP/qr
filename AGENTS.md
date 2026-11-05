# AGENTS.md

Conventions for this repo. Read before editing anything.

## What this is

File & text → QR code, and QR image decoding. One project of My
Playground; the hub lives in the `playground` repo at
`https://tsp-playground.netlify.app/`.

The repo is the whole project: published page, tests, prototypes, planning.
Only `site/` is public.

## Publishing target: Netlify → `site/`

Netlify publishes `site/` (set in `netlify.toml`) to
`https://tsp-qr-maker.netlify.app/` on every push to `main`. The rules below are
constraints of that target and apply to `site/` only. Everything outside
`site/` may use whatever it needs. An idea that conflicts with them is out of
scope for the published page, not rejected: say so, note it for later, and
don't refuse or water down the idea.

- **No build step.** Serve `site/` and it works. No bundler, no framework.
- **Client-side only.** Pages is static: no backend, no secrets.
- **No CDN dependencies.** Third-party libraries are vendored into
  `site/vendor/` with their license intact.
- **Vanilla everything.** Plain HTML, CSS and ES5-compatible JS in an IIFE.
- **Self-contained.** Nothing in `site/` may reference files outside it.

## Layout

```
site/                published page
  index.html
  assets/style.css   copy of the playground shell (see Styling)
  assets/theme.js    light/dark/system switch (shell copy)
  vendor/            vendored third-party libs
  *.js               page modules
tests/               browser test pages; load code from ../site/
prototypes/          experiments, not published
docs/roadmap.md      planning
```

## Planning

- For QR features or limits, read `docs/roadmap.md`.
- QR brainstorming starts in
  `C:\D\Obsidian\First Vault\Notes\File-to-QR-Code-Conversion.md`; move settled
  decisions into the roadmap so the repo remains authoritative.

## Styling

`site/assets/style.css`, `site/assets/theme.js` and `site/assets/fonts/` are copies of the shared
playground shell, so the page looks like the rest of the site. Design
decisions for the whole site family are in the hub repo's
`docs/design-brief.md`. Use its custom properties (`--ink`, `--bg`,
`--panel`, `--line`, `--accent`, `--muted`); never hard-code a color that has a
token — dark mode is driven entirely by those tokens. Page-specific CSS goes in
the page's `<style>` block, not the shared file, so the copy stays easy to
resync with the hub.

The one deliberate exception: QR output stays pure `#000` on `#fff` regardless of
theme, because scanners need the contrast.

## SEO

The page needs a `<title>`, `<meta name="description">` written for the search
query a real person would type, and a canonical link to
`https://tsp-qr-maker.netlify.app/`. The copy is the product.

## Honesty in the UI

State real limits in the interface rather than failing mysteriously. The page
shows a live byte counter against the true capacity and explains the ~2 KB
ceiling instead of silently truncating.

## Testing

No test framework. Serve the repo root (so `tests/` can reach `../site/`), open
the pages in `tests/`, and exercise `site/` in a browser — the happy path plus
at least one boundary or error case. `file://` will not work.

## Commits

Imperative subject line, body explaining why. Do not commit `node_modules`,
build output, or agent scratch files.
