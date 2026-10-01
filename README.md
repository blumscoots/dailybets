# Daily Bets Board

A static GitHub Pages site that shows the day's researched bets across six sports — baseball, football, soccer, hockey, golf and basketball — plus a mixed **Best of the Day** section. Each sport has **Straight**, **Parlay** and **Player Props** tabs, and every pick carries odds, stake, confidence, reasoning and source links.

## Setup (once)

1. Create a new public repo on GitHub (e.g. `dailybets`).
2. Upload `index.html` and the `data/` folder (with `picks.json` inside) to the repo root.
3. Settings → Pages → Source: **Deploy from a branch**, branch `main`, folder `/ (root)`. Your site goes live at `https://<username>.github.io/dailybets/`.

## Daily refresh

1. In Claude, ask: **"Refresh my daily bets board for today."**
2. Claude researches the slate and gives you a new `picks.json`.
3. In the repo, open `data/picks.json` → pencil icon (or "Add file → Upload files") → replace it → commit.
4. Reload the site (it busts the cache automatically).

Only `data/picks.json` changes day to day — `index.html` stays the same.

## Data format

```
sections[] → { id, label, icon, slate, straight[], parlay[], props[] }
straight/props item → { pick, market, odds, units, confidence (1–5), event, time, reasoning, sources[] }
parlay item → { title, legs[{pick, odds, event}], units, confidence, sgp, reasoning }
```

Parlay odds and the "$10 pays" figure are calculated on the page from each leg's odds. Same-game parlays (`sgp: true`) are flagged because books price those lower than the multiplied odds.

## Read this

Picks are research-backed, not guaranteed. Lines move — check the current price before betting. Bet only what you can afford to lose. Help: 1-800-GAMBLER.
