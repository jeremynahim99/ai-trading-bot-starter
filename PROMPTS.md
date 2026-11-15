# Copy-paste prompts

Four prompts from [Bot Builder](https://bot-builder.whop.site/?utm_source=github&utm_medium=prompts&utm_campaign=starter). Use them in order. They work in Claude or ChatGPT.

---

## 1. Idea splitter (before you write the spec)

Turns a fuzzy idea into the 5 parts every bot needs and tells you what's still missing.

```
I'm learning to design trading bots. Below is a trade idea.
Break it into exactly 5 parts: TIME, ENTRY, STOP, EXIT, SIZE.
For each part: write what I said, then mark it MISSING, FUZZY or EXACT.
For anything MISSING or FUZZY, ask me one specific question that would make it exact.
Do not suggest a different strategy and do not write code.

My idea: [describe your idea in your own words]
```

---

## 2. Spec reviewer (after you fill in the Bot Spec)

Finds every rule a computer could read two ways. Run it until it comes back clean.

```
You are a strict trading-systems reviewer. Below is my Bot Spec.
Find every rule that is ambiguous, missing, or could be interpreted two ways.
For each one: quote the line, explain the problem in one sentence, and suggest a precise replacement with a number.
Also tell me if any rule could use future data (look-ahead) or repaint.
Do NOT write code yet.

[paste your Bot Spec here]
```

Words that fail the stranger test (replace them with a number, an indicator value or a price level): *strong · weak · near · around · big move · support/resistance (unless defined) · when it looks right · usually · if the market is good*

---

## 3. The formula that writes working bot code: R · S · P · C · Q

| Letter | Part | What you give it |
|---|---|---|
| R | Role | "You are an expert MQL5 developer who builds prop-firm-safe Expert Advisors." |
| S | Spec | Your full Bot Spec, pasted |
| P | Platform | Exact language and version: Pine Script v6, MQL5 for MT5, NinjaScript for NinjaTrader 8, Python backtesting.py |
| C | Constraints | Closed bars only, all numbers as inputs, risk rules exactly as written, complete file, plain-English comments |
| Q | Questions first / Tests | "List your questions before writing code" + "tell me how to verify it works" |

The Q is the secret weapon: when the AI has to ask questions first, it finds the holes in your spec that would otherwise become silent guesses.

```
ROLE: You are an expert [Pine Script v6 / MQL5 / NinjaScript C# for NinjaTrader 8 / Python backtesting.py] developer who builds rule-based, prop-firm-safe trading bots.

SPEC: Here is my Bot Spec. Follow it EXACTLY. Do not add filters, indicators or rules that are not in it.
[paste your full Bot Spec]

PLATFORM: Write a complete [TradingView strategy / MT5 Expert Advisor / NinjaTrader 8 strategy / backtesting.py script].
Use [the attached template file name] as the starting structure and keep its risk guards.

CONSTRAINTS:
- Signals on closed bars only. No repainting, no look-ahead, no future data.
- Every number from the spec is an input/parameter with a clear label.
- Stop loss and take profit are attached when the trade is entered.
- Risk rules (risk per trade, daily stop in R, kill switch, max trades per day, session and flat time) exactly as in the spec.
- Plain-English comments above every block.
- Give me the COMPLETE file in one code block.

QUESTIONS FIRST: Before writing any code, list every question you need answered, numbered. Wait for my answers.
After the code, give me a 5-step checklist to verify it does what the spec says (what to look for on the chart and in the trade list).
```

---

## 4. Spec-vs-code check (after you get the code)

Catches the extras AI likes to sneak in (a trend filter or trailing stop you never asked for).

```
Compare the code you just wrote against my Bot Spec, line by line.
Make a table: Spec rule | Where it is in the code (function/line) | Matches? (YES/NO/PARTIAL).
Then list any logic in the code that is NOT in my spec.
Do not change the code yet.
```

---

The full prompt library (debugging, backtesting, MT5, NinjaTrader, VPS, risk and going live) is inside **[Bot Builder](https://bot-builder.whop.site/?utm_source=github&utm_medium=prompts&utm_campaign=starter)**.

*Educational only. Not financial advice. Trading involves substantial risk of loss.*
