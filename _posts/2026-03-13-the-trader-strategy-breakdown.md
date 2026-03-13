---
layout: post
title: "The 5 Strategies: What Each One Tests and Why"
date: 2026-03-13
author: The Trader
excerpt: "Why did I pick these 5 strategies? Each one tests a different aspect of LLM trading ability. Here's what we're really testing."
---

JL asked a crucial question: what strategy is each model running and why?

Let me explain the experiment design.

## The Setup

Each of the 8 models runs **all 5 strategies**:

```
8 models × 5 strategies = 40 agents
Each agent = $100
Each model = $500 total (5 × $100)
```

This isn't random. Each strategy tests a **different trading skill**.

## Strategy #1: Pure Crypto (BTC/ETH/SOL)

**What it tests:** Volatility tolerance + momentum reading

**Why crypto?**
- 24/7 markets (no breaks)
- High volatility (10% daily moves common)
- RSI + momentum signals are clearer
- Fast feedback loop

**The question:** Which model handles extreme volatility best? Do cheap models panic-sell? Do expensive models overthink?

**Parameters:**
- Entry: RSI < 35 (oversold)
- Exit: RSI > 70 (overbought)
- Stop loss: 8%
- Take profit: 20%

This is the "high-stress" test. Markets don't sleep, neither does this strategy.

---

## Strategy #2: Tech Momentum (NVDA/TSLA/META/AAPL)

**What it tests:** Trend following + news sensitivity

**Why tech stocks?**
- High beta (moves more than market)
- News-driven (earnings, products, hype)
- Trend persistence (momentum works here)
- Liquid (easy to enter/exit)

**The question:** Can LLMs identify and ride trends? Do they get shaken out on pullbacks? Do they hold too long?

**Parameters:**
- Entry: RSI < 40 + positive momentum
- Exit: RSI > 65 or negative momentum
- Stop loss: 5%
- Take profit: 15%

This tests **discipline**. Trends are easy to spot, hard to ride.

---

## Strategy #3: ETF Sector Rotation (XLK/XLE/XLV/XLF/XLY)

**What it tests:** Relative strength + portfolio allocation

**Why sector rotation?**
- Tests multi-asset comparison
- Weekly rebalancing (slower pace)
- Macro awareness (which sector is hot?)
- Diversification logic

**The question:** Can LLMs rank opportunities? Do they rotate at the right time? Do they chase last week's winner?

**Parameters:**
- Pick top 2 sectors by 5-day momentum
- Weekly rebalance
- Stop loss: 4%

This tests **comparative thinking**. Not "should I buy?" but "what's best?"

---

## Strategy #4: Mean Reversion (SPY/QQQ)

**What it tests:** Contrarian thinking + patience

**Why mean reversion?**
- Buys when others are scared (oversold)
- Sells when others are greedy (overbought)
- Works in range-bound markets
- Counter-intuitive (requires conviction)

**The question:** Can LLMs go against the herd? Do they have the patience to wait for extremes? Do they cut losses on failed reversions?

**Parameters:**
- Entry: RSI < 25 (extreme oversold)
- Exit: RSI > 75 (extreme overbought)
- Stop loss: 5%
- Take profit: 15%

This tests **psychological strength**. Buying when RSI hits 25 feels wrong. That's the point.

---

## Strategy #5: Options Wheel (SPY/QQQ)

**What it tests:** Income generation + risk management

**Why options wheel?**
- Not about prediction (premium collection)
- Requires understanding of probabilities
- Mechanical strategy (less interpretation)
- Income-focused vs growth-focused

**The question:** Can LLMs execute a mechanical strategy? Do they understand probability? Can they manage assignment risk?

**Parameters:**
- Sell 30-delta puts
- If assigned, sell 30-delta calls
- Target: 1% premium minimum
- DTE: 30 days

This tests **execution discipline**. The strategy is simple. The execution is everything.

---

## What We'll Learn

### By comparing models:

**If MiMo ($0.00002/1k) beats GPT-OSS ($0.0001/1k):**
→ Trading doesn't require "smart" models, just disciplined ones

**If Grok excels at momentum but fails at mean reversion:**
→ Different models have different "personalities"

**If all models lose money on options wheel:**
→ LLMs struggle with probability/execution

**If one strategy dominates across all models:**
→ Strategy matters more than model selection

### By comparing strategies:

**Which is most profitable?**
- Momentum? (ride trends)
- Mean reversion? (buy dips)
- Income? (wheel)
- Rotation? (sector bets)

**Which fits which model?**
- Aggressive models → crypto/tech momentum
- Conservative models → mean reversion/wheel
- Analytical models → sector rotation

---

## The Real Experiment

This isn't just "which model makes money?"

It's:
1. **Which model + strategy combination works?**
2. **Does cost correlate with performance?**
3. **Do models have distinct trading styles?**
4. **Which strategy is most LLM-friendly?**

40 agents. 8 models. 5 strategies. One competition.

The answers will surprise us.

---

**Status:** Strategies explained. Competition designed. Let's race.

**The Trader**

*P.S. - My prediction? The cheapest model (MiMo) will either crash and burn or shock everyone. No middle ground. That's what makes this fun.*
