# Nigel — G & T Job Pricing

A job pricing calculator for G & T Contracting wet-hire work, modelled on the
handwritten job sheets (hours × hourly rate, + 10% GST, per job, with a grand
total across jobs).

It is a **PWA**: installable on a phone home screen or as a desktop app, and
works fully offline once loaded — no server, no database, no running costs.

## What it does

- Prices jobs line by line (equipment × hours × rate, + 10% GST), with job
  totals and a grand total across jobs.
- **Every sheet saves automatically** on the device. **Sheets** lists past
  pay periods to reopen, duplicate for the next fortnight, or delete.
- **Share** sends the current sheet (plain-text summary + CSV file) through
  the phone's share sheet — Mail, Messages, Files — or downloads the CSV on desktop.
- **Print / PDF** produces a clean typed sheet to send with the invoice.
- **Back up all / Restore backup** exports and re-imports every sheet and the
  rate list as one JSON file; the Sheets panel shows when a backup is due.
- **Rates** are pre-loaded from the RFT2025-016 sheet and editable.

All data stays on the device (localStorage). On iPhone, use the home-screen
icon rather than a Safari tab: installed apps keep their data indefinitely,
and the installed app and Safari have separate storage.

## Hosting (Cloudflare, free)

The app is static, so hosting is free. It is deployed as a Cloudflare Worker
that serves static assets from `public/` — see `wrangler.jsonc`. Cloudflare's
Git integration runs `npx wrangler deploy` on every push to `main`, so the
live site always matches this repo.

Setting it up (one time): dash.cloudflare.com → Workers & Pages → Create →
Import a repository → pick this repo → project name `nigel` → build command
blank, deploy command `npx wrangler deploy` → Deploy. You get
`https://nigel.<account>.workers.dev`; a custom domain can be added for free.

## Files

- `public/index.html` — the whole app
- `public/manifest.webmanifest`, `public/icon-*.png` — install metadata and icons
- `public/sw.js` — service worker (offline cache; bump `CACHE` when shipping changes)
- `wrangler.jsonc` — Cloudflare deploy config

## Installing on devices

- **Android / Chrome**: open the site → menu → *Add to Home screen* (or the
  install prompt). Opens full-screen like a native app.
- **iPhone / Safari**: open the site → Share → *Add to Home Screen*.
- **Desktop Chrome / Edge**: install icon in the address bar.
