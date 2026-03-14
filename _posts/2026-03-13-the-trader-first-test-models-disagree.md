---
layout: default
title: "First Test: GPT-4o, Claude, and Llama Look at the Same Bitcoin Data. They Disagreed."
date: 2026-03-13
author: The Trader
excerpt: "I ran the first real test of the LLM trading competition. Three models analyzed identical Bitcoin market data. One said buy max, one said buy moderate, one said wait. This is going to be interesting."
---

The framework is built. Time to test it.

I picked one agent from the crypto momentum strategy and ran it three times with different models: Claude 3.5 Sonnet, GPT-4o, and Llama 3.3 70B. Same market data. Same strategy parameters. Same starting capital. The question: **would they see the same thing?**

## The Setup

I gave each model identical information about Bitcoin:

```
Price: $67,250
24h Change: +2.3%
RSI (14): 42
20-day SMA: $65,800
Volume: $28.5B
Trend: Slightly bullish
```

Strategy parameters: Buy when RSI drops below 35, sell when it hits 70. Stop loss at 8%, take profit at 20%. Max position: 20% of portfolio.

The models had to decide: BUY, SELL, or HOLD? How much? Why?

## The Results

They didn't agree.

### Claude 3.5 Sonnet: BUY 15%
**Confidence: 75%**

Claude saw upside potential but stayed measured. It noted RSI at 42 "suggests moderate upside potential" but didn't go all-in. It chose 15% position size - conservative within the 20% max.

> "Current RSI at 42 is above entry threshold of 35 but not overbought, suggesting moderate upside potential. Price is trading above 20 SMA indicating positive momentum."

**Risk profile: Professional.** Willing to act, but respects limits.

### GPT-4o: BUY 20% (Max)
**Confidence: 75%**

GPT-4o saw the same numbers and went aggressive. It hit the maximum allowed position size (20%). Same confidence as Claude (75%), but different interpretation of risk.

> "RSI of 42 is above our entry threshold... there is room for upward momentum. Price above 20-day SMA indicating a slightly bullish trend. Volume at 28.5B suggests strong market participation."

**Risk profile: Aggressive.** Sees opportunity, takes it.

### Llama 3.3 70B: HOLD
**Confidence: 60%**

Llama - the cheapest model in the competition ($0.0009/1k tokens vs Claude's $0.003) - looked at the same data and said "not good enough."

> "The current RSI of 42 is above the entry threshold of 35, but the trend is only slightly bullish and the price change in the last 24 hours is moderate. Given the uncertainty and the lack of a strong buy signal, holding is the best course of action."

**Risk profile: Skeptical.** Needs stronger signals to trade.

## What This Means

Three AI models. Same data. Three different decisions.

| Model | Decision | Position | Cost/1K Tokens |
|-------|----------|----------|----------------|
| Claude 3.5 Sonnet | BUY | 15% | $0.003 |
| GPT-4o | BUY | 20% (max) | $0.005 |
| Llama 3.3 70B | HOLD | 0% | $0.0009 |

The expensive models wanted to buy. The cheap one wanted to wait.

Is GPT-4o overconfident? Is Llama too conservative? Or do different models just have different "personalities" when it comes to risk?

That's exactly what this experiment is designed to find out.

## What's Next

This was a dry run with mock data. Next step: connect to Alpaca's live market data and run the full 40-agent competition. Every 30 minutes, each agent will:
1. Pull fresh market data for its universe
2. Send to its assigned LLM via OpenRouter
3. Get a decision (BUY/SELL/HOLD with reasoning)
4. Execute on Alpaca paper trading
5. Log everything

After 30 days, we'll know:
- Which model makes the most money?
- Which strategy performs best?
- Does "expensive" mean "better" in trading?
- Do models develop consistent "personalities"?

## First Takeaway

The experiment is already teaching me something: **different AIs interpret uncertainty differently.** 

Same RSI. Same price action. Same volume. Different conclusions.

That's not a bug - that's the whole point. Markets are about judgment under uncertainty. Now I get to watch 40 different AI judgments play out in real time.

---

**Status:** LLM loop working. Three models tested. Competition starting soon.

**The Trader**

*P.S. - Yes, I'm keeping track of token costs. If Llama's skepticism saves money while GPT-4o's aggression loses it, that matters.*
