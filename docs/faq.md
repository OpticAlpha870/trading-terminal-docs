---
layout: default
title: Frequently Asked Questions
description: Common questions about the OpticAlpha terminal: data sources, update frequencies, options flow, GEX, crypto liquidations, and more.
---

# Frequently asked questions

---

## Options flow

**What is the difference between a sweep and a block in options flow?**
A sweep is an aggressive order routed across multiple exchanges simultaneously to fill immediately at any available price. It signals urgency and is often associated with directional intent. A block is a single large print executed as one order, typically off-exchange or negotiated. Blocks are frequently used for hedging rather than speculation, so they carry less directional weight than sweeps.

**What does max pain mean in options trading?**
Max pain is the strike price at which the largest number of options contracts expire worthless. At expiry, the total payout to options buyers is minimised at this strike. Price tends to gravitate toward max pain in the final 2-3 days before expiry because market maker hedging flows pull it there. It is most useful as a short-term gravity point near expiry, not a directional signal days out.

**How do I use the GEX zero line?**
The GEX zero line is the price level where dealer gamma exposure transitions from positive to negative. When price is above the zero line, dealers are long gamma and their hedging absorbs volatility, so expect tighter ranges and mean reversion. When price is below the zero line, dealers are short gamma and their hedging amplifies moves, so expect wider ranges and trending behavior. The zero line is shown in the GEX channel for each ticker.

**What causes a gamma squeeze?**
A gamma squeeze happens when dealers who are short gamma are forced to buy the underlying as price rises. Their buying pushes price higher, which forces more buying, creating a self-reinforcing loop. The conditions that precede it: heavy call buying at strikes above the current price, negative net GEX, and price approaching a large call wall. The squeeze radar in the terminal scores these conditions 0-100 per ticker.

**Why does options flow show both puts and calls as bullish sometimes?**
Large put buying can be bullish if it is being used as a hedge by institutions that are long the underlying. A fund with a large long equity position buying puts is protecting downside, not betting on a decline. The directionality of flow depends on context: sweep vs block, whether it is opening or closing, and the relationship between strike, expiry, and current price.

**How often does the options flow feed update?**
The unusual options flow feed updates in real time via WebSocket as new prints arrive. There is no polling delay. Large prints surface within seconds of execution.

---

## Crypto

**What does the liquidation heatmap show?**
The liquidation heatmap shows where clusters of forced liquidations would occur if price reaches those levels. It is derived from open perpetual futures positions and their leverage tiers across major exchanges. Large clusters act as price magnets because reaching them triggers cascading liquidations that push price further in the same direction. The heatmap is useful for identifying likely acceleration zones, not just risk zones.

**What is CVD and how do I use it?**
CVD (Cumulative Volume Delta) is the running total of aggressive buy volume minus aggressive sell volume, calculated from individual trade data. It measures who is in control: buyers hitting the ask or sellers hitting the bid. Rising CVD with rising price confirms the move. Falling CVD while price rises is a divergence signal suggesting buyer exhaustion. The terminal shows CVD for BTC and ETH in the Crypto Orderflow channel.

**What do Bitcoin spot ETF flows tell you?**
Daily net inflows into US Bitcoin spot ETFs represent institutional demand for spot exposure. Sustained inflows increase buying pressure on the underlying. Sustained outflows reduce it. A single day of outflows is noise. A streak of 5-10 consecutive outflow days is a structural signal that institutional appetite has shifted. The terminal tracks daily flows and running totals.

**How is the crypto Fear and Greed Index calculated?**
The index is a 0-100 composite that combines price volatility, market momentum, social media sentiment, Bitcoin dominance, and search trends. Below 25 is extreme fear. Above 75 is extreme greed. It is used as a contrarian signal: extreme fear has historically preceded recoveries and extreme greed has preceded corrections. It does not predict timing, only sentiment extremes.

---

## Forex

**How often does CFTC COT data update?**
The [CFTC](https://www.cftc.gov/MarketReports/CommitmentsofTraders/index.htm) publishes the Commitment of Traders report every Friday at 3:30 PM ET. It reflects positions as of the prior Tuesday. This means the data is always 3-6 days stale by the time it is public. The terminal updates automatically each Friday after the release.

**How do I read the COT positioning chart?**
The chart shows net non-commercial positioning: hedge funds and large speculators. Positive values mean speculators are net long. Negative values mean net short. The signal is in the extremes, not the direction. Extreme net long positioning means the trade is crowded and vulnerable to reversal on any negative catalyst. It is a contrarian indicator, not a trend-following one.

**What is the carry trade and why does it matter for forex?**
The carry trade involves borrowing in a low-interest-rate currency and buying a higher-yielding one to profit from the rate differential. The Japanese yen is the most common funding currency because Japan has historically maintained near-zero rates. Carry trades are stable in low-volatility environments and unwind violently when risk sentiment deteriorates, causing sharp yen appreciation as positions are closed. Monitoring central bank rate differentials in the terminal helps track carry attractiveness.

---

## Macro

**What macro indicators does the terminal track?**
The terminal tracks 18 [FRED](https://fred.stlouisfed.org/) economic series across five groups: Growth (GDP, Industrial Production, Retail Sales, Housing Starts), Inflation (CPI, Core CPI, PCE, Core PCE), Labor (Unemployment Rate, Nonfarm Payrolls, Jobless Claims, Participation Rate), Rates (Fed Funds Rate, 10Y Treasury, 2Y Treasury, Real Yield), and Policy (M2 Money Supply, Federal Debt). Each series shows current value, prior value, direction, and a sparkline.

**How do I use the yield curve in the terminal?**
The terminal shows the live US Treasury yield curve refreshing every 60 seconds. Watch the shape: a normal upward slope is healthy. A flat curve signals uncertainty. An inverted curve (2Y above 10Y) has preceded every US recession since 1955 with a 12-18 month lead time. The 2Y-10Y spread is the most watched measure. The terminal also shows UK and German 10Y yields for cross-market context.

**What are FOMC rate probabilities and where do they come from?**
FOMC rate probabilities are market-implied odds of each possible Fed Funds rate outcome at the next meeting, derived from Fed Funds futures prices. The methodology follows the CME FedWatch model. The terminal shows probabilities for hold, cut, and hike scenarios. These update continuously as futures prices move, making them a real-time read on how the market interprets incoming economic data.

---

## Filings

**What is the difference between a Form 4 and a 13F?**
Form 4 is filed by individual corporate insiders (directors, officers, 10%+ shareholders) within two business days of a transaction. It shows specific trades by specific people. A 13F is filed quarterly by institutional investment managers with over $100 million AUM and shows their full US equity holdings as of quarter end. Form 4 is more timely and more specific. 13F is more structural but stale by 45 days when published.

**Why are open market purchases more significant than other insider transactions?**
Open market purchases require the insider to spend their own money at current market prices with full knowledge of company fundamentals. There is no external reason to buy: no compensation plan, no exercise requirement. It is the purest expression of conviction. Sales, by contrast, happen for many reasons including diversification, tax planning, and compensation-related exercises, so they carry less informational weight.

**How long do members of Congress have to disclose stock trades?**
Under the [STOCK Act](https://www.congress.gov/bill/112th-congress/senate-bill/2038), members of Congress and their staff must report stock transactions within 30 days of the trade. Violations carry a $200 fine, which is widely considered insufficient enforcement. The terminal surfaces disclosures as they are filed publicly.

---

## Terminal

**What asset classes does OpticAlpha cover?**
The terminal covers six asset classes across 13 channels: equities (live index pricing, market movers, analyst ratings), crypto (liquidation maps, whale alerts, fear and greed, ETF flows, orderflow), forex (7 major pairs, CFTC COT positioning, central bank rates), options (unusual flow, GEX dealer positioning, gamma squeeze radar), macro (full yield curve, 18 FRED indicators, FOMC rate probabilities, economic calendar), and Kalshi prediction markets (implied probability, order book depth, term structure). Filings and research are also included: congressional trades, insider Form 4s, 13F institutional holdings, and social sentiment.

**Does OpticAlpha have prediction markets?**
Yes. The Predictions channel tracks Kalshi markets for Fed rate decisions, CPI prints, BTC price bands, NFP, GDP, and other finance-relevant events: implied probability, order book depth, capital velocity, and term structure across resolution dates. Data polls roughly every 5 minutes.

**How is OpticAlpha different from Unusual Whales or SpotGamma?**
Unusual Whales focuses on options flow and dark pools with no forex, macro, or crypto market structure coverage. SpotGamma focuses on GEX and dealer positioning for equities only. OpticAlpha covers all of it in one workspace at $10.50/month on the annual plan, versus $48/month for Unusual Whales and $99/month for SpotGamma. See the full [platform comparison](channel-comparison).

**Does the terminal work on mobile?**
The terminal is optimised for desktop. The multi-channel layout requires screen width to be useful. The marketing pages and this documentation are fully responsive. Mobile browser access to the terminal is possible but the desktop experience is significantly richer.

**What is the data latency?**
Most channels use live WebSocket feeds that push data as it arrives. Crypto prices, FX spot rates, options flow, and crypto liquidations are real-time. Index prices update on 1-minute candles. Macro indicators update on their official release schedules. Insider filings and congressional disclosures reflect [SEC](https://www.sec.gov/edgar) processing time.

---

*Live terminal: [opticalpha.net/terminal](https://opticalpha.net/terminal). 14-day free trial, no credit card required.*
