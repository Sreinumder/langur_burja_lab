# Langur Burja Lab

A single-file, offline-friendly Langur Burja (Crown & Anchor) tracker for recording rolls, shake sequences, stakes, and outcomes.

## Files

| File | Status |
| --- | --- |
| [`langur_burja_lab_v3.html`](langur_burja_lab_v3.html) | Current version |
| [`langur_burja_lab_v2.html`](langur_burja_lab_v2.html) | Older version, kept for reference |

## Run

Open `langur_burja_lab_v3.html` directly in a modern browser. No build step, server, or dependency is required.

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
- **v2** — Older standalone version retained for reference.
