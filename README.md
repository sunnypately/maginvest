# Strategic Co-Investment Tracker

A single-file institutional-style equity research dashboard tracking strategic equity stakes and material partnerships disclosed by NVIDIA, AMD, Broadcom, Alphabet, Amazon, Meta and Apple — with live quotes and a real-time deal-news feed across all 20 tickers in scope.

## Live Demo

Once deployed via GitHub Pages: `https://<your-username>.github.io/co-investment-tracker/`

## Features

**Positions tab.** 13 co-investment positions organized into three tiers — highest conviction (COHR, NTNX, TLN, INTC, NOK), high conviction with execution dependencies (BE, CRDO, TSM, MU, CRWV, NBIS), and speculative single-counterparty exposure (RIVN, GSAT). Each card shows live quotes (price, day high/low, open, prev close, % change), strategic-investor badges, deal-term grid (stake size, strike price, contract value, etc.), thesis paragraph, and bull/bear case framing.

**Live deal news tab.** Pulls Finnhub's `company-news` endpoint across all 20 tickers on a 14-day rolling window. Articles are deduped (one entry per article, even if cross-tagged on multiple tickers), sorted newest first, and capped at 80 items. Four filter chips: All, Parent Cos, Positions Only, and High-Signal (pattern-matches partnership/acquir/invest/stake/equity/multibillion/PPA/warrant/MOU/LTA/etc.). Quotes auto-refresh every 60s; news refreshes every 5min when the tab is open.

**Aesthetic.** Dark terminal theme (`#0f0f0f` background, `#c9a84c` gold accent), Libre Baskerville for editorial typography, JetBrains Mono for UI chrome. Single-file self-contained HTML — no build step, no dependencies beyond Google Fonts CDN.

## Quick Start

Clone, then open `index.html` in any modern browser:

```bash
git clone https://github.com/<your-username>/co-investment-tracker.git
cd co-investment-tracker
open index.html
```

## Deploy to GitHub Pages

1. Create a new GitHub repository named `co-investment-tracker` (or whatever you prefer).
2. Push this folder:
   ```bash
   git init
   git add .
   git commit -m "Initial commit — v2.0"
   git branch -M main
   git remote add origin https://github.com/<your-username>/co-investment-tracker.git
   git push -u origin main
   ```
3. In the repo settings, navigate to **Pages**, set source to **Deploy from a branch**, select `main` / `/ (root)`, and save.
4. Your dashboard will be live at `https://<your-username>.github.io/co-investment-tracker/` within a minute or two.

## Configuration

The Finnhub API key is currently embedded inline near the top of the `<script>` block in `index.html`:

```js
const FINNHUB_KEY = 'd7g12c1r01qqb8rhuptgd7g12c1r01qqb8rhupu0';
```

Free Finnhub tier limits are 60 calls/minute. The dashboard makes ~20 quote calls per refresh cycle and ~20 news calls (only when the news tab is opened), throttled at 80ms between calls. To use a different key, replace the string above. To rotate keys without committing them, fork the repo into a private mirror or move the key to a runtime config endpoint behind a proxy.

## Project Structure

```
co-investment-tracker/
├── index.html          # The full dashboard — single self-contained file
├── README.md           # This file
├── LICENSE             # MIT
└── .gitignore          # Standard ignores
```

## Conviction Framework

Each position is rated on a five-star conviction scale based on:
- Quality and recency of the strategic-capital disclosure (equity stake > supply commitment > customer relationship)
- Concentration and visibility of contracted revenue
- Valuation entry point relative to comparable names
- Asymmetry of upside/downside relative to position size
- Execution risk and time-to-catalyst

Tier I (4–5★) names have fresh, large-dollar disclosures and high-asymmetric setups. Tier II (3–4★) are consensus longs where the thesis is real but partly priced in. Tier III (1–2★) are speculative single-counterparty bets that should be sized small.

## Data Sources

- **Live quotes:** [Finnhub.io](https://finnhub.io) `/quote` endpoint
- **Live news:** Finnhub `/company-news` endpoint
- **Deal terms:** Public 8-K filings, press releases, 13F holdings reports, earnings call transcripts (sourced manually, embedded in the HTML)

## Disclaimer

This is not investment advice. Strategic equity stakes from corporate parents reflect commercial alignment, not pure investment-return targets. All positions require independent due diligence; valuation, position sizing, tax placement, and concentration risk are determinations only the holder of capital can make. Past performance is not indicative of future results.

## License

MIT — see `LICENSE`.

---

**Built with:** vanilla JS · vanilla CSS · zero build pipeline
**Renders on:** any browser that supports `fetch` and CSS Grid (effectively every browser since 2018)
