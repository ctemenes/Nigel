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

## Files

- `index.html` — the whole app
- `manifest.webmanifest`, `icon-*.png` — install metadata and icons
- `sw.js` — service worker (offline cache; bump `CACHE` when shipping changes)

## Free hosting (recommended: Cloudflare Pages)

The app is static, so hosting is free. Because this repo is private,
use a host with free private-repo deploys:

1. Sign up at https://dash.cloudflare.com (free plan).
2. Workers & Pages → Create → Pages → **Connect to Git** → pick this repo.
3. Build settings: no build command; leave **Build output directory** as `/` (the app sits at the repo root).
4. Deploy — you get `https://<name>.pages.dev`, HTTPS included, auto-redeploys
   on every push. Custom domains are free too.

Netlify's free tier works the same way (publish directory `/`).
GitHub Pages also works, but only if the code lives in a **public** repo.

## Installing on devices

- **Android / Chrome**: open the site → menu → *Add to Home screen* (or the
  install prompt). Opens full-screen like a native app.
- **iPhone / Safari**: open the site → Share → *Add to Home Screen*.
- **Desktop Chrome / Edge**: install icon in the address bar.
