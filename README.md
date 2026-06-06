# OpticAlpha — Trading Terminal Documentation

Technical reference for the [OpticAlpha](https://opticalpha.net) real-time market data terminal.

---

## Data Channels

OpticAlpha runs 12 data channels, each streaming over a dedicated WebSocket connection. Cards update in real time as new data arrives.

---

### 1. News

Live market headlines, a USD economic calendar with actual vs forecast vs prior values, and FedWatch rate probabilities showing FOMC meeting outcome probabilities across hold, cut, and hike scenarios.

**Use case:** Pre-market monitoring, economic event timing, rate trajectory before trading rate-sensitive sectors.

---

### 2. Equities

Live index prices for SPY, QQQ, and DIA with 1-minute candlestick charts. VIX spot level. Fear & Greed gauge (0-100) with 7-day history. Top gainers, losers, gap ups and gap downs. AI-generated market brief. Earnings calendar with EPS estimates.

**Use case:** Start-of-day context, volatility regime check, gap scanner for pre-market setups.

---

### 3. Options

Real-time unusual options flow feed showing sweeps, blocks, and whale prints with premium, volume, and open interest. Max pain chart for SPY, QQQ, and DIA by nearest expiry. Active options table ranked by total notional with relative notional and put/call breakdown. On-demand GEX (gamma exposure) analysis per ticker.

**Key concepts:**
- **Sweep:** Aggressive multi-exchange order, often directional
- **Block:** Single large print
- **Whale:** Very large premium trade
- **Max pain:** Strike where most contracts expire worthless, acts as a price gravity point near expiry
- **GEX zero line:** Boundary between low-vol (dealers long gamma, absorb moves) and high-vol (dealers short gamma, amplify moves) regimes

**Use case:** Directional signals from flow, pinning levels near expiry, gamma regime identification.

---

### 4. Crypto

BTC and ETH live prices with 1-minute candlestick charts and volume. Crypto Fear & Greed gauge. Liquidation heatmap showing forced liquidation clusters by price level and leverage tier. Live liquidation feed. Whale alerts from large perpetual trades. Bitcoin spot ETF daily flows. Crypto segment performance by narrative (Layer 1, DeFi, Layer 2, AI tokens, etc.).

**Key concepts:**
- **Liquidation heatmap:** Shows where cascading forced sells/buys would occur if price reaches those levels. Large clusters act as price magnets, not just risk zones.
- **CVD (Cumulative Volume Delta):** Running total of buy volume minus sell volume. Rising CVD confirms aggressive buying. Divergence between price and CVD signals exhaustion.

**Use case:** Liquidation level targeting, ETF flow as institutional demand signal, segment rotation tracking.

---

### 5. Crypto Orderflow

Binance order book depth for BTC and ETH showing real-time bid/ask ladders. Cumulative Volume Delta (CVD) from aggregated trade data.

**Use case:** Order book imbalance for scalping, CVD divergence as exhaustion signal.

---

### 6. Macro

Live US yield curve (2Y, 3M, 10Y) plus UK and German 10Y for cross-market context. 18 FRED economic indicators across five groups:

- **Growth:** GDP, Industrial Production, Retail Sales, Housing Starts
- **Inflation:** CPI, Core CPI, PCE, Core PCE
- **Labor:** Unemployment Rate, Nonfarm Payrolls, Jobless Claims, Participation Rate
- **Rates:** Fed Funds Rate, 10Y Treasury, 2Y Treasury, Real Yield
- **Policy:** M2 Money Supply, Federal Debt

Each series shows current value, previous value, direction, and a sparkline.

**Use case:** Macro regime identification, Fed policy context, yield curve shape as cycle indicator.

---

### 7. Forex

Live spot rates for 7 pairs: EURUSD, USDJPY, GBPUSD, USDCAD, AUDUSD, USDCHF, NZDUSD. 30-day price history with ATR calculated as a percentage of spot. CFTC COT non-commercial net positioning as a bar chart — extremes signal potential reversals, not continuation. Central bank policy rates with historical rate path. Economic calendar covering all 8 FX-relevant currencies.

**Key concepts:**
- **COT non-commercial:** Hedge funds and large speculators. Extreme one-sided positioning = reversal risk.
- **ATR as % of spot:** Used for position sizing. If EURUSD ATR is 60 pips, a 120-pip target requires 2x ATR conviction.

**Use case:** Carry trade context, speculator positioning for reversal setups, ATR-based position sizing.

---

### 8. Filings

Congressional stock trades reported under the STOCK Act, showing politician name, party, chamber, ticker, transaction type, and amount range. Insider transactions from SEC EDGAR Form 4 filings — open market purchases and sales only, minimum $100,000, 30-day rolling window. Sourced directly from SEC EDGAR, not a third-party provider.

**Key concepts:**
- **Open market buy:** Highest-quality insider signal. Requires public disclosure, comes with legal restrictions.
- **10b5-1 plan:** Pre-scheduled trades that carry less informational value than discretionary open market buys.

**Use case:** C-suite open market buys as conviction signals, congressional sector positioning clues.

---

### 9. Institutions

Aggregate view of all 13F institutional filings from SEC EDGAR — most added, most reduced, new positions, and fully closed positions for the current quarter. Per-fund holdings trend search showing position changes across multiple quarters.

**Note:** 13F data is quarterly with a 45-day filing lag. Shows where institutional money was 6-7 weeks ago — useful for structural positioning, not short-term signals.

**Use case:** Institutional convergence signals (multiple funds opening same position), fund rotation tracking.

---

### 10. Company Intel

On-demand per-ticker research: financial health score, revenue and earnings trends, peer comparison, analyst consensus rating, recent upgrades and downgrades, price target history, and GEX analysis by strike.

**Use case:** Pre-trade research, analyst sentiment, dealer gamma positioning for a specific name.

---

### 11. Socials

WallStreetBets trending tickers ranked by mention count with 24-hour momentum. Short squeeze watchlist showing short float percentage, days to cover, and mention count.

**Use case:** Retail attention spikes on high-short-interest names as squeeze setup indicators.

---

### 12. AI Algo Wars

Simulated paper trading competition between AI models. Each model has a portfolio, P&L, and recent trade history. Entertainment feature, not a trading signal.

---

## Update Frequency Reference

| Channel | Fastest update |
|---|---|
| Crypto prices | Real-time |
| FX spot rates | Real-time |
| Options flow | Real-time |
| Crypto liquidations | Real-time |
| Index prices | 1-minute candles |
| VIX | ~60 seconds |
| Yield curve | ~60 seconds |
| Fear & Greed | Hourly |
| Economic calendar | Daily |
| Crypto ETF flows | Daily |
| CFTC COT | Weekly |
| FRED macro series | Monthly |
| Institutional 13F | Quarterly |
| Congressional trades | Days after filing |
| Insider Form 4 | Days after filing |

---

## Links

- Terminal: [opticalpha.net/terminal](https://opticalpha.net/terminal)
- Blog: [opticalpha.net/blog](https://opticalpha.net/blog)
- X: [@opticalpha870](https://x.com/opticalpha870)
- Bluesky: [opticalpha.bsky.social](https://bsky.app/profile/opticalpha.bsky.social)
- LinkedIn: [linkedin.com/company/opticalpha](https://www.linkedin.com/company/opticalpha)
- Telegram: [t.me/opticalpha](https://t.me/opticalpha)
- Threads: [@opticalpha_](https://www.threads.com/@opticalpha_)
