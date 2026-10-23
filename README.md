# Langur Burja Lab

A single-file, offline-friendly Langur Burja tracker for recording rolls, shake sequences, stakes, and outcomes.

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

- Record six dice per roll, with a configurable shake sequence; the last sequence is ready for the next roll, and tapping a method starts a new one
- Custom shake methods and editable face order
- Stake presets with editable `500` / `1000` values
- Payout rule selection and automatic return/net calculation
- Full scrollable roll history with 24-hour times, outcome colors, and bet markers; a back-to-latest button appears when you scroll away from the newest roll
- Delete controls only appear when history details are expanded; compact rows have no delete crosses
- Full-detail history rows showing shakes, money, per-shape bets, next-pick hit/miss, and notes
- Face frequency shown in the history header
- Winner-to-next-winner analysis for rolls with 2+ matching dice
- Next-roll picks with estimated hit chance, plus window checks for the last 5, last 15, and a custom last N rolls
- Guess accuracy tracking for the next-roll picks, with the latest hit/miss and per-roll results in history details
- Settings tab with shake logic off by default, and a custom analysis window (N)
- Overview tab with recorded-roll stats
- Cumulative profit/loss chart with peak and maximum-drawdown summaries
- You-vs-computer accuracy charts for single picks and 50/50 two-shape picks, using your saved bets and the next-roll model
- Shake method, sequence-length, and length-transition statistics with plain-language reading guides
- CSV export dialog with a renameable title/place and a compact, copyable guide to the rules, payouts, and CSV columns
- CSV import to restore or merge a previous export; duplicate rolls are skipped
- Guarded delete-all action
- Local browser storage with migration from older storage keys

## Notes

- Data is stored in the browser's `localStorage`; it is not uploaded anywhere.
- Next-roll picks are a statistical signal, not a guarantee.
- **Shake logic is off by default.** Shake sequence and length are still recorded in history, but next-roll picks ignore them until you enable the setting. When enabled, shake-length outcomes are included again.
- **Chance** is a blended estimate that a shape reaches 2+ on the next roll, based on the active data. The window check recalculates it for the last 5, last 15, and custom last N rolls; small windows are noisy.
- **You vs computer** uses your saved bets for your side: a single pick is exactly one backed shape; a 50/50 pick is exactly two backed shapes with stakes within Rs. 1 of each other. The computer uses the same next-roll model as the picks card. A hit means at least one pick reaches 2+, and only rolls where both sides had a pick are compared.
- Guess accuracy counts a hit when at least one suggested shape reaches 2+ on the next saved roll.
- **Export CSV** opens a dialog where the title (usually the place where you play) becomes both the file name and the `table` column. The same dialog has a copyable guide to the rules, payouts, shape names, and CSV columns.
- **Import** accepts a CSV exported by this app, adds the rows to the current log, skips duplicate rolls, and restores the payout rule and title where possible.
- Export important data with **Export CSV** before clearing browser storage.

## Version History

- **v3** — Current version: full scrollable history with back-to-latest, Settings with shake logic off by default, 5/15/N next-roll window checks with estimated chance, Overview stats, profit/loss chart, and you-vs-computer accuracy graphs; plus pick accuracy tracking, dice-state-aware next-roll picks, CSV import, renameable export title, copyable rules/CSV guide, last-sequence carry-over, redesigned history, header face frequency, and 2+ winner transition analysis.
- **v2** — Previous standalone version. Removed from the current tree; it remains available in git history.
