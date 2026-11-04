# QR

File & text → QR code, and QR image decoding, entirely in the browser.
Live at https://tsp-qr-maker.netlify.app/.

## Layout

```
site/          the published page (Netlify serves this folder)
tests/         browser test pages
prototypes/    experiments
docs/          planning
```

## Local preview

```
npx serve .
```

Then open `/site/` for the page or `/tests/` for the test pages.

## Deploy

Push to `main`; Netlify publishes `site/` (set in `netlify.toml`). Other
branches and pull requests get Netlify preview URLs.
