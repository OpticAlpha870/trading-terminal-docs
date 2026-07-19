---
layout: default
title: Trading Terminal Glossary
description: Definitions for GEX, CVD, max pain, COT, liquidation maps, gamma squeeze, and 30+ other terms used in the OpticAlpha market data terminal.
---

# Trading terminal glossary

Definitions for terms used across the OpticAlpha terminal. Each entry covers what the term means, the mechanic behind it, and how it surfaces in the terminal.

---

## Options and gamma

**GEX (Gamma Exposure)**
A measure of how much market makers must buy or sell the underlying asset to stay delta-neutral as price moves. Positive GEX means dealers are long gamma and absorb volatility. Negative GEX means dealers are short gamma and amplify moves. The GEX zero line is the boundary between these two regimes.

**DEX (Delta Exposure)**
The aggregate directional bias of all options positioning. Positive DEX implies dealers are net long the underlying, creating a bullish lean. Negative DEX implies net short. Shown per strike in the GEX channel.

**Max pain**
The strike price at which the largest number of options contracts (both puts and calls) expire worthless. At expiry, price gravitates toward max pain because it minimises total payout to options buyers. Most relevant in the final 2-3 days before expiry.

**Call wall**
The strike with the highest concentration of call gamma. Acts as overhead resistance because dealers must sell the underlying as price approaches it to hedge their short delta exposure.

**Put wall**
The strike with the highest concentration of put gamma. Acts as support because dealers must buy the underlying as price approaches it to hedge their long delta exposure.

**Zero gamma line**
The price level where net GEX transitions from positive to negative. Above it: low volatility, price tends to mean-revert. Below it: high volatility, price moves get amplified by dealer hedging flows.

**Squeeze radar**
A composite score (0-100) measuring how close a ticker is to conditions that historically precede a gamma squeeze. Combines GEX sign, flow direction, short interest, and price position relative to key strikes.

**Gamma squeeze**
When dealers short gamma are forced to buy the underlying aggressively as price rises, which pushes price higher, which forces more buying. Self-reinforcing loop that causes rapid price acceleration.

**Options sweep**
An aggressive options order routed across multiple exchanges simultaneously to fill quickly at any available price. Associated with informed or directional intent. Contrasts with a passive limit order sitting on one exchange.

**Block trade**
A single large options print executed as one order, typically off-exchange or negotiated. Large premium, not necessarily directional: can be hedging.

**Whale print**
Very large premium options trade, regardless of structure. Defined by notional size relative to normal activity in that ticker.

**Open interest (OI)**
The total number of outstanding options contracts that have not been settled or closed. High OI concentration at a strike creates structural support or resistance as dealers hedge those positions.

**Put/call ratio**
Total put volume divided by total call volume. Above 1 means more put activity. Below 1 means more call activity. Useful as a sentiment indicator but not directional on its own: puts are used for both hedging and bearish bets.

**Expected move**
The market-implied price range for a stock by a given expiry, derived from at-the-money options pricing. Roughly equals the straddle price. The terminal shows this for major indices.

---

## Crypto

**Liquidation heatmap**
A visualisation of where forced liquidations would cluster if price reaches certain levels. Derived from open perpetual futures positions and their leverage tiers. Large liquidation clusters act as price magnets because reaching them triggers cascading forced sells or buys that push price further.

**CVD (Cumulative Volume Delta)**
The running total of aggressive buy volume minus aggressive sell volume, calculated from individual trade data. Rising CVD confirms buyers are in control. Falling CVD confirms sellers. Divergence between price and CVD signals exhaustion: price making new highs while CVD falls means buyers are losing conviction.

**Perpetual futures**
Cryptocurrency futures contracts with no expiry date. The funding rate mechanism keeps the perpetual price anchored to spot. Positive funding means longs pay shorts (market is bullish and leveraged). Negative funding means shorts pay longs.

**Funding rate**
The periodic payment between long and short holders of perpetual futures. Extreme positive funding indicates overleveraged longs and increases squeeze risk to the downside. Extreme negative funding indicates overleveraged shorts.

**Crypto Fear and Greed Index**
A 0-100 composite sentiment gauge for crypto markets. Below 25 is extreme fear, above 75 is extreme greed. Historically, extreme fear has preceded recoveries and extreme greed has preceded corrections. Used as a contrarian signal.

**Whale alert**
A large transaction on-chain or in perpetuals, typically above a threshold that suggests institutional or large-account activity. In the terminal, whale alerts surface large perpetual trades on BTC and ETH.

**Bitcoin spot ETF flows**
Daily net inflows and outflows from US-listed Bitcoin spot ETFs. Sustained outflows reduce spot buying pressure. Sustained inflows increase it. Tracked as an institutional demand signal.

**Orderbook depth**
The full ladder of outstanding bid and ask orders at each price level. Imbalances between bid and ask depth indicate short-term directional pressure. Large walls on one side can act as temporary support or resistance.

---

## Forex

**COT (Commitment of Traders)**
A weekly report published by the CFTC every Friday, covering positions as of Tuesday that week. Shows net positioning of non-commercial traders (hedge funds and large speculators), commercial traders (hedgers), and small speculators. The non-commercial net position is the primary signal traders use.

**Non-commercial positioning**
The aggregate net long or short position of hedge funds and large speculators in a futures market. Extreme one-sided positioning historically precedes reversals, not continuation, because the trade is crowded. Used as a contrarian signal, not a momentum signal.

**COT extreme**
When non-commercial net positioning reaches a multi-year high or low. No precise threshold, but visually obvious on a chart. Historically associated with trend exhaustion in that currency pair.

**Carry trade**
Borrowing in a low-interest-rate currency to buy a higher-yielding one, profiting from the rate differential. JPY is the most common funding currency. Carry trades unwind rapidly when risk sentiment deteriorates, causing sharp moves in the funding currency.

**ATR (Average True Range)**
A measure of average daily price movement over a rolling period. In the terminal, ATR is expressed as a percentage of spot price to allow cross-pair comparison. Used for position sizing: a 60-pip ATR on EURUSD means a 120-pip target requires 2x normal ATR conviction.

**Central bank rate**
The benchmark interest rate set by a country's central bank. Differentials between central bank rates are a primary driver of currency pair direction over medium timeframes. The terminal tracks rates for the Fed, ECB, BOE, BOJ, BOC, RBA, and RBNZ.

---

## Macro

**Yield curve**
A plot of US Treasury yields across maturities, typically 2Y, 5Y, 10Y, 30Y. A normal curve slopes upward (longer maturities yield more). An inverted curve (2Y yielding more than 10Y) has historically preceded recessions by 12-18 months. The terminal shows the live curve refreshing every 60 seconds.

**Yield curve inversion**
When short-term Treasury yields exceed long-term yields. The 2Y-10Y spread is the most watched measure. Persistent inversion signals that markets expect the Fed to cut rates in the future, implying expectations of economic slowdown.

**FRED indicators**
Economic data series published by the Federal Reserve Bank of St. Louis. The terminal surfaces 18 series across growth, inflation, labor, rates, and policy. Updated on official release schedules.

**Core PCE**
Personal Consumption Expenditures price index excluding food and energy. The Federal Reserve's preferred inflation measure. Monthly release. More stable than CPI, which is why the Fed targets it.

**NFP (Non-Farm Payrolls)**
Monthly US employment report released on the first Friday of each month. One of the most market-moving data releases. Large beats push yields and the dollar higher. Large misses do the opposite.

**FOMC rate probabilities**
Market-implied probabilities of each possible Fed Funds rate outcome at the next FOMC meeting, derived from Fed Funds futures pricing. Shown in the terminal as a bar chart across hold, cut, and hike scenarios. Tracked via the CME FedWatch methodology.

---

## Filings

**Form 4**
SEC filing required when a corporate insider (director, officer, or 10%+ shareholder) buys or sells company stock. Must be filed within two business days of the transaction. Open market purchases are the highest-quality signal: the insider is spending their own money with full knowledge of company fundamentals.

**10b5-1 plan**
A pre-scheduled trading plan set up in advance, typically when the insider does not have material non-public information. Sales under a 10b5-1 plan carry less informational signal than discretionary open market transactions because they were scheduled months earlier.

**13F filing**
Quarterly report required from institutional investment managers with over $100 million in assets under management. Shows all US equity holdings as of quarter end. Filed within 45 days of quarter end, meaning the data is 6-7 weeks stale by the time it is public. Useful for structural positioning signals, not short-term signals.

**STOCK Act**
Stop Trading on Congressional Knowledge Act. Requires members of Congress and their staff to disclose stock trades within 30 days of the transaction. Disclosures are public and tracked in the terminal.

**Congressional trade**
A stock transaction reported under the STOCK Act by a sitting member of Congress or their spouse. Not necessarily based on non-public information, but sector concentration patterns across multiple members can signal policy direction.

---

## Prediction markets

**Implied probability**
A prediction market's YES/NO contract price read directly as a probability. A contract trading at 62c implies the market assigns a 62% chance to that outcome. Moves with new information the same way an options-implied probability does.

**Term structure (predictions)**
How implied probability shifts across contracts with different resolution dates for the same underlying event. For example, a Fed rate-cut market priced differently for the next meeting versus the one after. Divergence between near and far contracts signals where the market expects the resolution of uncertainty to land.

**Capital velocity**
A measure of how fast money is rotating through a prediction market. High velocity on a thin market can move implied probability sharply on modest volume.

---

## Terminal-specific

**WebSocket feed**
A persistent connection between the terminal and the data server that pushes new data as it arrives, without the client needing to request it. Most real-time channels in the terminal use WebSockets. Contrasts with polling, where the client requests data on a fixed interval.

**Channel**
One of the 13 distinct data streams in the OpticAlpha terminal. Each channel has its own card, its own data source, and its own update frequency.

**Squeeze radar score**
A 0-100 composite score generated per ticker measuring proximity to gamma squeeze conditions. 80+ indicates strong setup. Combines GEX sign, net flow direction, price position relative to call wall, and short interest data.

---

*Full terminal documentation: [github.com/OpticAlpha870/trading-terminal-docs](https://github.com/OpticAlpha870/trading-terminal-docs)*

*Live terminal: [opticalpha.net/terminal](https://opticalpha.net/terminal). 14-day free trial, no credit card required.*
