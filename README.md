# AI Trading Bot Starter

**Turn your trading idea into a bot with Claude or ChatGPT. No coding background needed.**

This repo is the free starter kit from [Bot Builder](https://bot-builder.whop.site/?utm_source=github&utm_medium=readme&utm_campaign=starter) by [Artillery Trades](https://instagram.com/artillerytrades). It gives you the one page every bot starts from (the Bot Spec), the prompts that turn it into working code, and a TradingView strategy template with risk guards already built in.

> Educational only. Not financial advice. Trading involves substantial risk of loss.

---

## A bot is just 5 rules

People think a trading bot is a genius AI that "reads the market." It isn't. It's a checklist a computer runs on every closed bar.

| Part | The question it answers | Textbook example |
|---|---|---|
| **TIME** | When am I allowed to trade? | 09:45–15:30 New York, flat at 15:55, max 2 trades/day |
| **ENTRY** | What exactly makes me get in? | 20 EMA above 50 EMA AND the bar's low touches the 20 EMA AND it closes above it |
| **STOP** | Where am I wrong? | 1 × ATR(14) from entry |
| **EXIT** | Where do I take profit (or leave)? | 2 × the stop distance, or flat at 15:55 |
| **SIZE** | How much do I risk? | 0.5% of the account per trade |

Miss any one of these and you don't have a bot. You have a hope.

---

## Quick start (15 minutes)

1. **Write your rules.** Open [`BOT_SPEC_TEMPLATE.md`](BOT_SPEC_TEMPLATE.md) and fill in sections 1–5 for one idea. Apply the *stranger test*: if a stranger read it, would they take the exact same trades as you, every time?
2. **Let AI attack your spec.** Paste it into Claude or ChatGPT with the reviewer prompt in [`PROMPTS.md`](PROMPTS.md). Fix every line it flags.
3. **Generate the code.** Use the R·S·P·C·Q prompt formula in [`PROMPTS.md`](PROMPTS.md). Start from [`pine/bot_strategy_template.pine`](pine/bot_strategy_template.pine) if you're on TradingView, then run the spec-vs-code check.

Then backtest it with honest costs before it ever touches real money.

---

## What's inside

| File | What it is |
|---|---|
| [`BOT_SPEC_TEMPLATE.md`](BOT_SPEC_TEMPLATE.md) | The one-page spec: identity, trading window, entry, exits, risk & size, testing plan, paste-ready prompt |
| [`PROMPTS.md`](PROMPTS.md) | 4 copy-paste prompts: idea splitter, spec reviewer, the code-writing formula, spec-vs-code check |
| [`pine/bot_strategy_template.pine`](pine/bot_strategy_template.pine) | TradingView (Pine Script v6) strategy template: EMA pullback example, ATR stop, R target, max trades/day, daily stop in R, session window, end-of-day flat, JSON webhook alerts |

---

## An honest warning about the template

The EMA pullback in the template is a **teaching bot, and it loses**. Tested on NQ 1-minute data from 2019–2024 with 1 point of round-trip costs, it finished at **−167.9R in-sample** (profit factor 0.88) and **−57.8R out-of-sample** (profit factor 0.92).

That's on purpose. A famous, sensible-looking idea with honest costs lost. Your job is to replace the entry rules with your own, test them the same way, and only keep what survives.

---

## Want the full step-by-step?

This starter is the first page of the process. **[Bot Builder](https://bot-builder.whop.site/?utm_source=github&utm_medium=readme&utm_campaign=starter)** takes you from "I've never coded" to a bot you designed, tested and running 24/5:

- 60 lessons across 10 modules
- Build on **TradingView, MetaTrader 5 or NinjaTrader 8**
- Backtesting in Python with free data, in-sample vs out-of-sample
- Code templates for Python, Pine, MQL5 and NinjaScript, with prop-firm guards (daily stop, kill switch, fixed risk)
- Running it on a VPS with alerts to your phone
- Prompt library, 5 starter strategies with full Bot Specs, and every GitHub repo from the reels

Built by an active-duty soldier and futures trader who couldn't watch charts on duty, so he built bots with AI instead.

👉 **[bot-builder.whop.site](https://bot-builder.whop.site/?utm_source=github&utm_medium=readme&utm_campaign=starter)**

Free repo links from every reel: [artillery-bot-course.vercel.app/links](https://artillery-bot-course.vercel.app/links) · Instagram: [@artillerytrades](https://instagram.com/artillerytrades)

---

## License

MIT. Use it, change it, share it. See [LICENSE](LICENSE).

*Educational only. Not financial advice. Past or backtested results don't guarantee future results. Trading involves substantial risk of loss. Always start on a demo account.*
