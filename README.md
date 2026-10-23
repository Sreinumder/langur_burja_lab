# Langur Burja Lab

A single-file, offline-friendly Langur Burja (Crown & Anchor) tracker for recording rolls, shake sequences, stakes, and outcomes.

## Project Files

| File | Purpose |
| --- | --- |
| [`langur_burja_lab_v3.html`](langur_burja_lab_v3.html) | Current application |
| [`vercel.json`](vercel.json) | Vercel static deployment config |
| [`README.md`](README.md) | Project documentation |

## Run Locally

Open `langur_burja_lab_v3.html` directly in a modern browser. No build step, server, or dependency is required.

If you prefer a local server:

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000/langur_burja_lab_v3.html>.

## Deploy on Vercel

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/Sreinumder/langur_burja_lab&project-name=langur-burja-lab)

### Import from GitHub

1. In Vercel, choose **Add New → Project**.
2. Import `Sreinumder/langur_burja_lab`.
3. Use **Other** as the framework preset.
4. Leave the build command empty and set the output directory to `.`.
5. Deploy.

`vercel.json` maps `/` to `langur_burja_lab_v3.html`, so the deployment root opens the tracker directly.

### Deploy with the Vercel CLI

```bash
npm install -g vercel
vercel
vercel --prod
```

No build step is required for this static site.

## Features

- Record six dice per roll, with a configurable shake sequence
- Custom shake methods and editable face order
- Stake presets with editable `500` / `1000` values
- Payout rule selection and automatic return/net calculation
- Compact 10-roll history with 24-hour times, outcome colors, and bet markers
- Full-detail history rows showing shakes, money, per-shape bets, and notes
- Face frequency shown in the history header
- Winner-to-next-winner analysis for rolls with 2+ matching dice
- Next-roll picks combining winner transitions, shake-length outcomes, recent form, win rates, and face frequency
- Shake method, sequence-length, and length-transition statistics
- CSV export and a guarded delete-all action
- Local browser storage with migration from older storage keys

## Notes

- Data is stored in the browser's `localStorage`; it is not uploaded anywhere.
- Next-roll picks are a statistical signal, not a guarantee.
- Export important data with **Export CSV** before clearing browser storage.

## Version History

- **v3** — Current version: redesigned history, header face frequency, 2+ winner transition analysis, and combined next-roll picks.
- **v2** — Previous standalone version. Removed from the current tree; it remains available in git history.
