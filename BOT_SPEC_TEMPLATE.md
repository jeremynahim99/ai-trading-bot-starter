# THE BOT SPEC — turn any trading idea into rules AI can code
*Bot Builder by Artillery Trades · fill this in BEFORE you open Claude or ChatGPT*

> The stranger test: if you handed this page to a stranger, would they take the exact same trades as you, every time? If not, keep editing.

---

## 1. Identity
| Field | Your answer | Example |
|---|---|---|
| Bot name | | EMA Pullback v1 |
| Platform | TradingView / MT5 / NinjaTrader / Python backtest | MT5 |
| Market & symbol | | MNQ (Micro Nasdaq) / US100.cash |
| Timeframe the rules read | | 5-minute bars |
| Time zone of all times below | | New York (exchange) |

## 2. When is the bot allowed to trade?
| Field | Your answer | Example |
|---|---|---|
| Entry window | | 09:45 – 15:30 |
| Flat (close everything) at | | 15:55 |
| Days | | Mon–Fri |
| Skip news? (which events, how long) | | Skip 2 min before/after CPI & FOMC |
| Max trades per day | | 2 |

## 3. Entry rules (write them as IF … AND … THEN)
**LONG:** IF ______________________ AND ______________________ THEN buy at ______
**SHORT:** IF ______________________ AND ______________________ THEN sell at ______

*Example — LONG: IF the 20 EMA is above the 50 EMA AND the bar's low touched the 20 EMA AND the bar closed above the 20 EMA THEN buy at the close of that bar.*

Indicators used (with exact settings): ____________________ *(e.g. EMA 20 on close, EMA 50 on close, ATR 14)*

## 4. Exit rules
| Field | Your answer | Example |
|---|---|---|
| Stop loss | | 1 × ATR(14) from entry |
| Take profit | | 2R (2 × the stop distance) |
| Trailing / break-even? | | No |
| Time exit | | Flat at 15:55 |
| Opposite signal closes trade? | | No |

## 5. Risk & size
| Field | Your answer | Example |
|---|---|---|
| Risk per trade | | 0.5% of balance (or $250) |
| How size is calculated | | contracts = risk $ ÷ (stop in points × $ per point) |
| Daily stop | | no new trades after −2R today |
| Kill switch | | stop the bot at −4% day / −8% total (firm limits 5% / 10%) |

## 6. Testing plan
| Field | Your answer | Example |
|---|---|---|
| Data & years | | NQ 5-min, 2019–2025 |
| In-sample (build) | | 2019–2022 |
| Out-of-sample (look once) | | 2023–2025 |
| Costs per round trip | | 1 point (commission + slippage) |
| Keep it if… | | out-of-sample > 0R after costs AND max drawdown < 15R |

## 7. Paste-ready prompt
Copy everything above, then add:

```
You are an expert [MQL5 / Pine Script v6 / NinjaScript C# / Python backtesting.py] developer.
Write a complete, compile-ready [Expert Advisor / strategy] that follows this Bot Spec EXACTLY.
Rules:
- Use only closed bars for signals (no repainting, no look-ahead).
- Put every number from the spec in an input/parameter.
- Add comments that explain each block in plain English.
- Include the risk & size rules, daily stop and kill switch exactly as written.
- If anything in the spec is ambiguous, list your questions FIRST and wait for my answers before writing code.
Bot Spec:
[paste here]
```
