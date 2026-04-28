# Basis — Average Cost Calculator

A simple, private cost-basis calculator for stocks. Works for **US** (NYSE/Nasdaq, USD) and **UK** (LSE, GBP or pence) markets.

- Calculates your **weighted-average price per share** across every buy
- **Plan-your-next-buy** simulator: see the new average before you place the order
- Fees are folded into the cost basis
- Currency display toggle: **$ USD · £ GBP · p (pence)**
- 100% client-side — your data is saved in `localStorage` and never leaves your browser
- No accounts, no analytics, no cookies, no API calls

## Run locally

It's just one HTML file. Open `index.html` in any modern browser, or serve the folder:

```bash
npx serve .
```

## Deploy to GitHub Pages (free, no rules broken)

This repo deploys with a single workflow — **no third-party APIs, no scraping, no proxies, no secrets required.** Everything is static and runs in the browser, which keeps you compliant with:

- **GitHub Pages Terms** — static-only, no server-side processing, well within bandwidth/usage limits
- **Yahoo / Google Finance ToS** — *not used*, so nothing to violate
- **GDPR / privacy law** — no personal data is collected or transmitted

### Steps

1. Create a new repo on GitHub (e.g. `basis-calculator`).
2. Push this folder to it:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/<you>/<repo>.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Build and deployment → Source: GitHub Actions**.
4. The included workflow at `.github/workflows/deploy.yml` runs on every push to `main` and publishes the site automatically.
5. Visit `https://<you>.github.io/<repo>/`.

That's it. No build step, no Node, no bundler.

## How the math works

Your average is a weighted average across all buys, with fees rolled in:

```
avg = (Σ shares × price + Σ fees) ÷ Σ shares
```

The "Plan your next buy" panel re-runs the same formula with your hypothetical buy appended, so you can see exactly where your basis lands before you click the button on your broker.

## Disclaimer

Informational only. Not financial or tax advice.
