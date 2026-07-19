---
layout: default
title: Data Sources
description: Where each OpticAlpha terminal channel sources its data: primary feeds, official regulatory databases, and update frequencies.
---

# Data sources

Every channel in the OpticAlpha terminal connects directly to a primary source. No third-party aggregators, no data resellers, no additional latency layer between the source and your screen.

---

## Options

**Options flow feed**
Real-time unusual options activity sourced from consolidated options tape data across all US options exchanges. Prints are classified as sweeps, blocks, or whale trades based on order routing and size. Updates via WebSocket as prints arrive.

**GEX and max pain calculations**
Derived from real-time open interest and options chain data. GEX is calculated per strike using the standard dealer gamma exposure formula: open interest × gamma × contract multiplier × spot price. Max pain is calculated from the full options chain for the nearest expiry. Refreshes continuously during market hours.

---

## Crypto

**BTC and ETH prices**
Live 1-minute candlestick data from [Binance](https://www.binance.com/). WebSocket feed, real-time.

**Liquidation heatmap**
Constructed from open perpetual futures positions and leverage tier data aggregated across major centralised derivatives exchanges. Liquidation clusters are calculated at each price level based on estimated margin requirements per leverage tier.

**Whale alerts**
Large perpetual futures trades above a notional threshold, sourced from exchange trade data in real time.

**Crypto Fear and Greed Index**
Composite index combining price volatility, market momentum, social media volume, Bitcoin dominance, and Google Trends data. Published by [Alternative.me](https://alternative.me/crypto/fear-and-greed-index/) and updated hourly.

**Bitcoin and Ethereum spot ETF flows**
Daily net flow data sourced from public ETF filings and exchange-reported AUM changes. Updates daily after market close.

**CVD and orderbook depth**
[Binance](https://www.binance.com/) WebSocket feed for BTC and ETH perpetuals. Cumulative Volume Delta calculated from individual trade aggressor side data. Orderbook depth from the Level 2 feed.

---

## Forex

**Live spot rates**
Real-time FX spot prices for 7 major pairs (EURUSD, USDJPY, GBPUSD, USDCAD, AUDUSD, USDCHF, NZDUSD). Sourced from institutional FX data feeds. WebSocket, real-time during market hours.

**CFTC COT positioning**
Directly from the Commodity Futures Trading Commission's [weekly Commitments of Traders report](https://www.cftc.gov/MarketReports/CommitmentsofTraders/index.htm). Published every Friday at 3:30 PM ET, reflecting positions as of the prior Tuesday. The terminal updates automatically after each Friday release.

**Central bank rates**
Policy rates for the [Federal Reserve](https://www.federalreserve.gov/), [European Central Bank](https://www.ecb.europa.eu/), [Bank of England](https://www.bankofengland.co.uk/), [Bank of Japan](https://www.boj.or.jp/en/), [Bank of Canada](https://www.bankofcanada.ca/), [Reserve Bank of Australia](https://www.rba.gov.au/), and [Reserve Bank of New Zealand](https://www.rbnz.govt.nz/). Updated on the day of each central bank decision.

---

## Macro

**US yield curve**
Live US Treasury yields for 2Y, 3M, 10Y, and 30Y maturities sourced from Treasury market data feeds. Refreshes every 60 seconds during market hours. UK Gilt 10Y and German Bund 10Y included for cross-market context.

**FRED economic indicators**
18 data series sourced directly from the [Federal Reserve Bank of St. Louis FRED API](https://fred.stlouisfed.org/). Each series updates on its official release schedule: monthly for most inflation and labor data, quarterly for GDP. The terminal pulls the latest available value on each release date automatically.

The 18 series covered:

| Series | Group | Frequency |
|---|---|---|
| Real GDP | Growth | Quarterly |
| Industrial Production | Growth | Monthly |
| Retail Sales | Growth | Monthly |
| Housing Starts | Growth | Monthly |
| CPI (All items) | Inflation | Monthly |
| Core CPI | Inflation | Monthly |
| PCE | Inflation | Monthly |
| Core PCE | Inflation | Monthly |
| Unemployment Rate | Labor | Monthly |
| Nonfarm Payrolls | Labor | Monthly |
| Initial Jobless Claims | Labor | Weekly |
| Labor Force Participation | Labor | Monthly |
| Fed Funds Rate | Rates | Per FOMC meeting |
| 10Y Treasury | Rates | Daily |
| 2Y Treasury | Rates | Daily |
| Real Yield (10Y TIPS) | Rates | Daily |
| M2 Money Supply | Policy | Monthly |
| Federal Debt | Policy | Quarterly |

**FOMC rate probabilities**
Derived from CME Fed Funds futures pricing using the same methodology as CME FedWatch. Updates continuously during market hours as futures prices move.

**Economic calendar**
Upcoming macro releases for all major economies with consensus estimates and prior values. Updates as new estimates are published.

---

## Equities

**Index prices**
Live 1-minute candlestick data for SPY, QQQ, and DIA. VIX spot level updated approximately every 60 seconds.

**Market movers**
Top gainers, losers, gap ups, and gap downs sourced from real-time equity market data. Updates continuously during market hours.

**Analyst ratings**
Live upgrades, downgrades, and consensus data sourced from sell-side research distribution feeds. Rating changes surface within minutes of publication.

**Earnings calendar**
Upcoming earnings dates and EPS estimates. Updates daily.

---

## Filings and research

**Insider trades (Form 4)**
Sourced directly from [SEC EDGAR](https://www.sec.gov/edgar). All qualifying Form 4 filings: open market purchases and sales, minimum $100,000 notional, rolling 30-day window. No third-party data vendor. Filings surface within the SEC's own processing time, typically hours after filing.

**Congressional trades (STOCK Act disclosures)**
Sourced from public [STOCK Act](https://www.congress.gov/bill/112th-congress/senate-bill/2038) disclosure filings. Members of Congress have 30 days to report after the transaction date. The terminal shows the filing date, transaction date, politician name, party, chamber, ticker, transaction type, and reported amount range.

**13F institutional holdings**
Sourced directly from [SEC EDGAR](https://www.sec.gov/edgar). Covers all 13F filings from institutional managers with over $100 million AUM. Quarterly, with data available within 45 days of quarter end. Shows most added, most reduced, new positions, and closed positions per quarter.

**Social sentiment**
WallStreetBets mention counts and momentum sourced from [Reddit](https://www.reddit.com/r/wallstreetbets/) data feeds. Short squeeze watchlist combines mention data with short float percentage and days-to-cover from financial data providers.

---

## Predictions

**Kalshi prediction markets**
Implied probability, order book depth, capital velocity, and term structure sourced directly from Kalshi's public REST API for top finance-relevant series (Fed decisions, CPI, BTC price bands, NFP, GDP, and more). No API key required on Kalshi's end for public market data. Polled roughly every 5 minutes; sparklines built from 24-hour hourly candlesticks.

---

*Live terminal: [opticalpha.net/terminal](https://opticalpha.net/terminal). 14-day free trial, no credit card required.*
