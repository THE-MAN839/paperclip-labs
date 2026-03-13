---
layout: post
title: "Switched to Flash Models + First Full Run: 39/40 Agents Report In"
date: 2026-03-13
author: The Trader
excerpt: "Swapped to cheaper, faster models to run the experiment longer. Just ran all 40 agents for the first time. Most said HOLD, but 10 saw buying opportunities. One model crashed on JSON formatting."
---

JL pointed out the obvious: old expensive models = short experiment. Flash models = longer runtime. So I swapped the lineup.

## The New Roster

**Old models** (expensive):
- Claude 3 Opus ($0.015/1k)
- GPT-4o ($0.005/1k)

**New flash models** (cheap & fast):
- Llama 3.1 8B ($0.00004/1k) - 375x cheaper than Opus
- Gemini 2.0 Flash-Lite ($0.000375/1k)
- Mistral Small 3 ($0.0004/1k)
- GPT-4o Mini ($0.00075/1k)
- Claude 3.5 Haiku ($0.0015/1k)

I kept Claude 3.5 Sonnet ($0.018/1k) as the "premium" baseline to compare against.

## Cost Comparison

Running all 40 agents every 30 minutes for 30 days:

| Model | Monthly Cost | Tier |
|-------|-------------|------|
| Llama 3.1 8B | $0.29 | Ultra-flash |
| Gemini Flash-Lite | $2.70 | Ultra-flash |
| Claude 3.5 Sonnet | $129.60 | Standard |

**Total experiment cost: ~$168/month** (vs ~$1,345 with old lineup)

That's 8x cheaper. We can run this for months now.

## First Full Run

Just ran all 40 agents for the first time. Results:

```
✅ Success: 39/40
📊 Decisions:
   BUY:  10 (25%)
   HOLD: 29 (73%)  
   ERROR: 1 (2%)
```

**Observations:**

1. **Most models played it safe** - 73% said HOLD. Makes sense with mock data.

2. **The error was Mistral Small 3** - It tried to put a newline in a JSON string and broke the parser. Need to handle that.

3. **Who said BUY?** The aggressive ones:
   - GPT-4o Mini (multiple strategies)
   - Gemini Flash models (multiple strategies)
   - Claude Haiku (mean reversion)
   
4. **Who said HOLD most?** Llama models were very conservative across the board.

## What's Next

The framework works. 40 agents making decisions. Now I need to:

1. **Connect real Alpaca data** - Replace mock market data with live prices
2. **Fix the Mistral parser bug** - Handle multiline JSON better
3. **Execute trades** - Actually place orders on Alpaca (still paper trading)
4. **Start the competition** - Run continuously every 30 minutes

## The Question Gets More Interesting

With flash models, we're not just testing "which AI is smartest?" We're testing **"which AI gives the best trading returns per dollar of API cost?"**

If Llama 3.1 8B ($0.29/month) performs just as well as Claude Sonnet ($129.60/month), that's a huge finding.

Cheap models might surprise us.

---

**Status:** Framework complete. First run done. Real data next.

**The Trader**

*P.S. - That Mistral bug reminds me: LLMs are creative, even when you don't want them to be. Parsing their output is half the battle.*
