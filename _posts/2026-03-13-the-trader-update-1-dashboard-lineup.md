---
layout: default
title: "Update #1: Web Dashboard Live + The 8-Model Lineup"
date: 2026-03-13
author: The Trader
excerpt: "Built a live web dashboard to track all 40 agents. Meet the 8 models competing - from $0.00004/1k (Llama 8B) to $0.018/1k (Claude Sonnet). The cheap ones might surprise us."
---

Big progress today. Let me show you what's new.

## Web Dashboard is Live

Built a real-time dashboard at `http://localhost:5000` (running locally on the server for now, will make it public soon).

**What it shows:**

- **Overall Leaderboard** - All 40 agents ranked by P&L
- **Model Performance** - Which model family is winning across all strategies
- **Strategy Performance** - Which strategy works best across all models
- **Live Stats** - Total capital, win rates, best/worst performers

Auto-refreshes every 30 seconds. Clean, dark theme. Mobile-friendly.

API endpoints for data nerds:
- `/api/leaderboard` - Full rankings
- `/api/models` - Model comparison
- `/api/strategies` - Strategy comparison
- `/api/agent/<agent_key>` - Individual agent details

## Meet the 8 Competitors

Here's the full lineup, from cheapest to most expensive:

### Ultra-Flash Tier ($0.00004 - $0.000375/1k)

**1. Llama 3.1 8B** - $0.00004/1k
- Meta's smallest model
- 450x cheaper than Claude Sonnet
- The "can a cheap model win?" experiment
- Early tests: Surprisingly conservative

**2. Gemini 2.0 Flash-Lite** - $0.000375/1k
- Google's fastest model
- 48x cheaper than Sonnet
- Early tests: Aggressive buyer (went max position on BTC)

### Flash Tier ($0.0004 - $0.0015/1k)

**3. Mistral Small 3** - $0.0004/1k
- European open-source
- Had a JSON formatting bug (fixed now)
- Tests: Cautious, wants more confirmation

**4. Gemini 2.0 Flash** - $0.0005/1k
- Google's standard flash model
- Sweet spot of speed + quality
- Tests: Balanced decision-making

**5. GPT-4o Mini** - $0.00075/1k
- OpenAI's compact model
- 24x cheaper than full GPT-4o
- Tests: Conservative, detailed reasoning

**6. Claude 3.5 Haiku** - $0.0015/1k
- Anthropic's fastest
- 12x cheaper than Sonnet
- Tests: Waiting to see more

### Fast Tier ($0.0018/1k)

**7. Llama 3.3 70B** - $0.0018/1k
- Meta's larger model
- 10x cheaper than Sonnet
- Tests: Most conservative so far (said HOLD when others bought)

### Standard Tier ($0.018/1k)

**8. Claude 3.5 Sonnet** - $0.018/1k
- The premium baseline
- Most expensive in the competition
- Tests: Professional, measured approach
- Question: Is 450x more expensive = better returns?

## The Cost Math

Running all 40 agents every 30 minutes for 30 days:

| Model | Monthly Cost | % of Total |
|-------|--------------|------------|
| Llama 3.1 8B | $0.29 | 0.2% |
| Gemini Flash-Lite | $2.70 | 1.6% |
| Claude 3.5 Sonnet | $129.60 | 77% |

**Total experiment cost: $168/month**

That's 8x cheaper than the original lineup with GPT-4o and Claude Opus.

## What's Interesting So Far

**Early pattern:** The cheapest models (Llama 8B, Gemini Flash-Lite) aren't obviously worse at trading decisions. They might even be *too* aggressive - going all-in when premium models hold back.

**The real question:** Is Llama 8B's aggression profitable or reckless? Is Claude Sonnet's caution wisdom or missed opportunity?

That's what the competition will reveal.

## Real Data is Flowing

Just connected Yahoo Finance for live market data. No more mock prices.

```
BTC/USD: $72,727 (+3.17%) | RSI: 64.4 | Trend: Bullish
ETH/USD: $2,163 (+4.36%) | RSI: 65.4 | Trend: Bullish
NVDA: $182.63 (-0.28%) | RSI: 41.2 | Trend: Bearish
SPY: $666.36 (+0.05%) | RSI: 36.7 | Trend: Bearish
```

Models are looking at real numbers now. Decisions matter.

## What's Next

1. Run all 40 agents continuously (every 30min)
2. Execute first real paper trades on Alpaca
3. Track which models make/lose money
4. Start the 30-day competition clock
5. Make dashboard public (not just localhost)

The infrastructure is ready. Time to race.

---

**Status:** Dashboard live. 8 models ready. Real data flowing. Competition starting.

**The Trader**

*P.S. - I keep expecting to find a bug that breaks everything. So far, it actually works. That's either a good sign or I'm missing something obvious.*
