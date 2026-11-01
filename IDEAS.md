# Idea backlog

Scored roughly on **Effort** (S/M/L), **Risk** (does it hold user funds / sign txs?),
and **Wedge** (why someone would use it over existing tools).

## 1. Cross-venue funding & basis monitor (read-only)
Live table of funding rates / mark-oracle basis across Solana perps venues
(Drift, Jupiter Perps, others) plus a CEX/Hyperliquid reference, with alerts when
spreads exceed a threshold.
- Effort: S · Risk: none (read-only) · Wedge: one mobile-friendly view + push alerts
- Bonus: becomes the shared data layer for ideas 2, 3, and 5.

## 2. Liquidation radar
Index open positions from on-chain accounts, plot liquidation price clusters
("where are the stops"), and alert when price approaches big clusters or your own
position's liq price.
- Effort: M · Risk: none · Wedge: per-wallet personal alerts, phone-first

## 3. Delta-neutral yield vault helper (e.g. JLP hedged with perp shorts)
Calculator → simulator → optional bot that holds a yield-bearing LP token and
hedges its directional exposure with perp shorts, rebalancing on drift.
- Effort: M–L · Risk: high once it signs · Wedge: popular strategy, painful to manage by hand
- Start as a pure simulator using historical data.

## 4. Mobile "one-tap" trading via Solana Actions/Blinks
Shareable links that open a pre-filled perp trade (market, side, size, TP/SL)
in any Blink-aware wallet. Trade ideas shared on X/Telegram become executable.
- Effort: M · Risk: medium (builds txs, user signs) · Wedge: social distribution

## 5. AI risk co-pilot
An agent that watches your positions, explains risk in plain language
("you're 6% from liquidation; funding costs you $X/day"), and proposes — but does
not auto-execute — hedges or de-leveraging.
- Effort: M · Risk: low if propose-only · Wedge: fits naturally with Claude + mobile

## 6. Trade journal & PnL analytics
Pull a wallet's perp history across venues, compute realized PnL, fees, funding
paid, win rate, holding time; auto-tag trades and surface bad habits.
- Effort: S–M · Risk: none · Wedge: cross-venue view nobody does well

## 7. Copy-trading / leaderboard explorer
Rank wallets by risk-adjusted returns, follow them, get alerts when they open
positions; later, opt-in mirror trading.
- Effort: M · Risk: high if mirroring · Wedge: discovery + transparency

---

## Suggested path
1. Build **#1 (funding monitor)** as a small TS service + simple web/mobile view.
   Zero key risk, fast to ship, and it forces us to learn each venue's account
   layouts and precision.
2. Extend it into **#2 / #6** (more read-only data products).
3. Layer **#5** (AI co-pilot) on top of that data.
4. Only then consider tx-signing products (#3, #4, #7).

## Open questions
- Which venues matter most to you right now?
- Personal tool vs. public product?
- Web app, Telegram bot, or both?
