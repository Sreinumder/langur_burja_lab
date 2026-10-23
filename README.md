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

- Record six dice per roll, with a configurable shake sequence; the last sequence is ready for the next roll, and tapping a method starts a new one
- Custom shake methods and editable face order
- Stake presets with editable `500` / `1000` values
- Payout rule selection and automatic return/net calculation
- Compact 10-roll history with 24-hour times, outcome colors, and bet markers
- Full-detail history rows showing shakes, money, per-shape bets, next-pick hit/miss, and notes
- Face frequency shown in the history header
- Winner-to-next-winner analysis for rolls with 2+ matching dice
- Next-roll picks combining last-winner transitions, the last roll's 0/1/2+ dice state, shake-length outcomes, recent form, win rates, and face frequency
- Guess accuracy tracking for the next-roll picks, with the latest hit/miss and per-roll results in history details
- Separate Strategy tab with a Rs. 5, 5, 10, 10, 20, 20, 50, 50, 100, 100, 200, 200 ladder, reset after a win, and a saved budget
- Two-shape plan with exact 6-dice odds, an automatic split of the next ladder rung, and an apply action
- Cumulative profit/loss chart with peak and maximum-drawdown summaries
- Shake method, sequence-length, and length-transition statistics
- CSV export dialog with a renameable title/place and a compact, copyable guide to the rules, payouts, and CSV columns
- CSV import to restore or merge a previous export; duplicate rolls are skipped
- Guarded delete-all action
- Local browser storage with migration from older storage keys

## Notes

- Data is stored in the browser's `localStorage`; it is not uploaded anywhere.
- Next-roll picks are a statistical signal, not a guarantee.
- **Strategy** reads the saved bet rolls: only consecutive losses advance the ladder, a win or breakeven resets it to Rs. 5, and no-bet rolls are ignored. The budget covers one full ladder cycle (Rs. 770 by default), not a guaranteed profit.
- **2-shape split** divides the next ladder total across the top two current picks. The odds panel uses the 6-dice model: 48.4% chance at least one of the two reaches 2+, and 26.3% for a specific shape. Splitting does not change the underlying house edge.
- Guess accuracy counts a hit when at least one suggested shape reaches 2+ on the next saved roll.
- **Export CSV** opens a dialog where the title (usually the place where you play) becomes both the file name and the `table` column. The same dialog has a copyable rules/payout/CSV guide.
- **Import** accepts a CSV exported by this app, adds the rows to the current log, skips duplicate rolls, and restores the payout rule and title where possible.
- Export important data with **Export CSV** before clearing browser storage.

## Version History

- **v3** — Current version: Strategy tab with a bankroll-aware ladder, two-shape plan, profit/loss chart, pick accuracy tracking, dice-state-aware next-roll picks, CSV import, renameable export title, copyable rules/CSV guide, last-sequence carry-over, redesigned history, header face frequency, and 2+ winner transition analysis.
- **v2** — Previous standalone version. Removed from the current tree; it remains available in git history.
