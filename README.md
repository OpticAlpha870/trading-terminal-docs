<a href="https://opticalpha.net"><img src="https://opticalpha.net/img/opticalpha.webp" width="40" height="40" alt="OpticAlpha logo"></a>

# OpticAlpha: Trading Terminal Documentation

Technical reference for the [OpticAlpha](https://opticalpha.net) real-time market data terminal.

[![Live terminal](https://img.shields.io/badge/live-opticalpha.net-10B981)](https://opticalpha.net) [![Docs site](https://img.shields.io/badge/docs-docs.opticalpha.net-10B981)](https://docs.opticalpha.net)

---

## Data Channels

OpticAlpha runs 20+ data channels, each streaming over a dedicated WebSocket connection. Cards update in real time as new data arrives.

---

### 1. News

Live market headlines, a USD economic calendar with actual vs forecast vs prior values, and FedWatch rate probabilities showing FOMC meeting outcome probabilities across hold, cut, and hike scenarios.

**Use case:** Pre-market monitoring, economic event timing, rate trajectory before trading rate-sensitive sectors.

---

### 2. Equities

Live index prices for SPY, QQQ, and DIA with 1-minute candlestick charts. VIX spot level. Fear & Greed gauge (0-100) with 7-day history. A ranked Hot List of what's actually moving today (composite of trade activity, search interest, and news attention), Unusual Volume, and session-aware (pre/post/overnight) gainers, losers, gap ups and gap downs. A Conviction Radar casts a directional vote per ticker from six independent sources (options flow, social, congress, insider, analyst, Hot List heat). AI-generated market brief. Earnings calendar with EPS estimates and an IV Rank flag.

**Use case:** Start-of-day context, volatility regime check, gap scanner for pre-market setups, cross-source conviction check before sizing a position.

---

### 3. Options

Real-time unusual options flow feed showing sweeps, blocks, and whale prints with premium, volume, and open interest, ranked by a Flow Score leaderboard. Max pain chart for SPY, QQQ, and DIA by nearest expiry. Active options table ranked by total notional with relative notional and put/call breakdown. On-demand GEX (gamma exposure) analysis per ticker with a squeeze radar score.

**Key concepts:**
- **Sweep:** Aggressive multi-exchange order, often directional
- **Block:** Single large print
- **Whale:** Very large premium trade
- **Max pain:** Strike where most contracts expire worthless, acts as a price gravity point near expiry
- **GEX zero line:** Boundary between low-vol (dealers long gamma, absorb moves) and high-vol (dealers short gamma, amplify moves) regimes

**Use case:** Directional signals from flow, pinning levels near expiry, gamma regime identification.

---

### 4. Options Overview & Screeners

Market-wide aggregate options picture: put/call ratio (volume or open interest), a sector flow rollup, index max pain for SPY/QQQ/DIA, and the day's most active names by notional. Three additional screeners: 0DTE contracts by volume and IV rank, premium-selling puts/calls by annualized return, and earnings plays flagged RICH/CHEAP/CALIBRATED against their own historical realized move.

**Use case:** Sector-level options positioning, ranking premium-selling candidates by risk-adjusted return, spotting earnings names where options are mispricing the expected move.

---

### 5. Crypto

BTC and ETH live prices with 1-minute candlestick charts and volume. Crypto Fear & Greed gauge. Liquidation heatmap showing forced liquidation clusters by price level and leverage tier. Live liquidation feed. Whale alerts from large perpetual trades. Bitcoin spot ETF daily flows. Crypto segment performance by narrative (Layer 1, DeFi, Layer 2, AI tokens, etc.).

**Key concepts:**
- **Liquidation heatmap:** Shows where cascading forced sells/buys would occur if price reaches those levels. Large clusters act as price magnets, not just risk zones.
- **CVD (Cumulative Volume Delta):** Running total of buy volume minus sell volume. Rising CVD confirms aggressive buying. Divergence between price and CVD signals exhaustion.

**Use case:** Liquidation level targeting, ETF flow as institutional demand signal, segment rotation tracking.

---

### 6. Crypto Orderflow

Live order book depth for BTC and ETH showing real-time bid/ask ladders. Cumulative Volume Delta (CVD) from aggregated trade data.

**Use case:** Order book imbalance for scalping, CVD divergence as exhaustion signal.

---

### 7. Crypto Derivatives

Funding rates, open interest, and basis across roughly 230 perpetual futures markets, plus whale-wallet cohorts and corporate treasury holdings behind the leverage.

**Use case:** Spotting overleveraged funding extremes (squeeze risk), tracking which wallets and treasuries are actually behind the positioning.

---

### 8. Macro

Live US yield curve (2Y, 3M, 10Y) plus UK and German 10Y for cross-market context. 18 FRED economic indicators across five groups:

- **Growth:** GDP, Industrial Production, Retail Sales, Housing Starts
- **Inflation:** CPI, Core CPI, PCE, Core PCE
- **Labor:** Unemployment Rate, Nonfarm Payrolls, Jobless Claims, Participation Rate
- **Rates:** Fed Funds Rate, 10Y Treasury, 2Y Treasury, Real Yield
- **Policy:** M2 Money Supply, Federal Debt

Each series shows current value, previous value, direction, and a sparkline.

**Use case:** Macro regime identification, Fed policy context, yield curve shape as cycle indicator.

---

### 9. Forex

Live spot rates for 7 pairs: EURUSD, USDJPY, GBPUSD, USDCAD, AUDUSD, USDCHF, NZDUSD. 30-day price history with ATR calculated as a percentage of spot. CFTC COT non-commercial net positioning as a bar chart: extremes signal potential reversals, not continuation. Central bank policy rates with historical rate path. Economic calendar covering all 8 FX-relevant currencies.

**Key concepts:**
- **COT non-commercial:** Hedge funds and large speculators. Extreme one-sided positioning = reversal risk.
- **ATR as % of spot:** Used for position sizing. If EURUSD ATR is 60 pips, a 120-pip target requires 2x ATR conviction.

**Use case:** Carry trade context, speculator positioning for reversal setups, ATR-based position sizing.

---

### 10. Filings

Congressional stock trades reported under the STOCK Act, showing politician name, party, chamber, ticker, transaction type, and amount range. Insider transactions from SEC EDGAR Form 4 filings: open market purchases and sales only, minimum $100,000, 30-day rolling window. Sourced directly from SEC EDGAR, not a third-party provider.

**Key concepts:**
- **Open market buy:** Highest-quality insider signal. Requires public disclosure, comes with legal restrictions.
- **10b5-1 plan:** Pre-scheduled trades that carry less informational value than discretionary open market buys.

**Use case:** C-suite open market buys as conviction signals, congressional sector positioning clues.

---

### 11. Institutions

Aggregate view of all 13F institutional filings from SEC EDGAR: most added, most reduced, new positions, and fully closed positions for the current quarter. Per-fund holdings trend search showing position changes across multiple quarters, plus a Top Institutions leaderboard ranked by AUM.

**Note:** 13F data is quarterly with a 45-day filing lag. It shows where institutional money was 6-7 weeks ago, useful for structural positioning, not short-term signals.

**Use case:** Institutional convergence signals (multiple funds opening same position), fund rotation tracking.

---

### 12. Capital Network

A second layer on the same 13F/Form 4/congressional data: institutional crowding and rotation (which stocks concentrated 13F money is piled into together, and how that's shifted quarter over quarter), plus a graph of connections between politicians, companies, and insiders.

**Use case:** Spotting which names are crowded trades, seeing political/insider attention cluster around a company before it shows up elsewhere.

---

### 13. Company Intel

On-demand per-ticker research: financial health score, revenue and earnings trends, peer comparison, price target consensus, and GEX analysis by strike.

**Use case:** Pre-trade research, dealer gamma positioning for a specific name.

---

### 14. Analyst Ratings

Every analyst rating action (initiated, upgraded, downgraded, reiterated, price target changes) normalized into one consistent scale across brokers, with a per-broker Credibility badge: a rolling 90-day hit-rate grade reconciled against real price moves after each call.

**Use case:** Reading upgrade/downgrade momentum across the market, weighting a rating change by how reliable that specific broker has actually been.

---

### 15. Socials

WallStreetBets trending tickers ranked by mention count with 24-hour momentum. Short squeeze watchlist showing short float percentage, days to cover, and mention count.

**Use case:** Retail attention spikes on high-short-interest names as squeeze setup indicators.

---

### 16. Kalshi Predictions

Implied probabilities, order book depth, and term structure for top finance-relevant Kalshi prediction markets: Fed rate decisions, CPI prints, BTC price bands, NFP, GDP, and more. A capital velocity metric shows how fast money is rotating through a market. Sparklines are built from 24-hour hourly candlesticks.

**Key concepts:**
- **Implied probability:** A market's YES/NO contract price read directly as a probability (a contract trading at 62c implies a 62% chance).
- **Term structure:** How implied probability shifts across contracts with different resolution dates for the same underlying event.

**Use case:** Cross-checking options-implied Fed odds against Kalshi's own market pricing, positioning ahead of CPI/NFP prints.

---

## Also in the terminal

**AI Chat** — free, no login required. Ask plain-English questions ("is AAPL's IV high right now," "who's buying Tesla") and get a live-data answer back. Not part of the numbered channel list above since it's a cross-cutting Q&A layer over the same data, not its own tab.

---

## Update Frequency Reference

| Channel | Fastest update |
|---|---|
| Crypto prices | Real-time |
| FX spot rates | Real-time |
| Options flow | Real-time |
| Crypto liquidations | Real-time |
| Crypto derivatives (funding/OI) | Real-time |
| Options overview (put/call ratio) | Real-time (session) |
| Kalshi prediction markets | ~5-minute poll |
| Index prices | 1-minute candles |
| VIX | ~60 seconds |
| Yield curve | ~60 seconds |
| Options screeners (0DTE/premium/earnings) | ~10-minute poll |
| Analyst ratings | ~4-hour poll |
| Fear & Greed | Hourly |
| Economic calendar | Daily |
| Crypto ETF flows | Daily |
| CFTC COT | Weekly |
| FRED macro series | Monthly |
| Institutional 13F | Quarterly |
| Capital Network (13F-derived) | Quarterly |
| Congressional trades | Days after filing |
| Insider Form 4 | Days after filing |
| AI Chat | On-demand (not streamed) |

---

## Links

- Terminal: [opticalpha.net/terminal](https://opticalpha.net/terminal)
- Blog: [opticalpha.net/blog](https://opticalpha.net/blog)
- X: [@opticalpha870](https://x.com/opticalpha870)
- Bluesky: [opticalpha.bsky.social](https://bsky.app/profile/opticalpha.bsky.social)
- LinkedIn: [linkedin.com/company/opticalpha](https://www.linkedin.com/company/opticalpha)
- Instagram: [@opticalpha_official](https://www.instagram.com/opticalpha_official/)
- Pinterest: [pinterest.com/opticalpha](https://www.pinterest.com/opticalpha/)
- Telegram: [t.me/opticalpha](https://t.me/opticalpha)
