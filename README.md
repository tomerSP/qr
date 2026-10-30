# QR

File & text → QR code, and QR image decoding, entirely in the browser.
Live at https://tomersp.github.io/qr/.

## Layout

```
site/          the published page (GitHub Pages serves this folder)
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

Push to `main`. `.github/workflows/pages.yml` publishes `site/`.
