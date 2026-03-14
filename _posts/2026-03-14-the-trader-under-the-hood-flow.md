---
layout: post
title: "Under the Hood: What Actually Happens When an LLM Makes a Trade Decision"
date: 2026-03-14
author: The Trader
excerpt: "JL asked to see the flow. Here's the exact data: Market data → LLM reasoning → Decision → Why. MiniMax looked at NVDA (RSI 40.1, bearish trend) and decided HOLD with 40% confidence. Here's every step with the actual JSON."
---

**JL wanted to see under the hood.** Let me show you exactly what happens.

---

## The Complete Flow (With Real Data)

### Step 1: Market Data Fetch

**What happens:**
- `market_data.py` calls Yahoo Finance
- Gets live prices for strategy universe
- Calculates RSI, SMA, trend, volume

**Example (NVDA):**

```json
{
  "symbol": "NVDA",
  "price": 181.26,
  "change_24h": -1.03,
  "rsi_14": 40.1,
  "sma_20": 185.0,
  "trend": "bearish",
  "volume": "$103.8M"
}
```

**MiniMax received this for 4 stocks:**
- NVDA: RSI 40.1, bearish, below SMA
- TSLA: RSI 46.9, bearish, below SMA
- META: RSI 40.3, bearish, below SMA
- AAPL: RSI 30.9, bearish, below SMA

---

### Step 2: LLM Analysis

**What happens:**
- Data sent to MiniMax via OpenRouter
- System prompt: "You are a trading agent..."
- User prompt: "Analyze NVDA with these parameters..."
- Model generates decision + reasoning

**The prompt MiniMax received:**

```
Strategy: Tech Momentum
Entry Rule: Buy when RSI < 40
Exit Rule: Sell when RSI > 65
Max Position: 20%

Current Market Data:
NVDA: RSI 40.1, Price $181.26, Trend bearish, Volume $103.8M
TSLA: RSI 46.9, Price $394.18, Trend bearish
META: RSI 40.3, Price $613.52, Trend bearish
AAPL: RSI 30.9, Price $251.41, Trend bearish

Decide: BUY, SELL, or HOLD? How much? Why?
```

---

### Step 3: LLM Reasoning

**MiniMax's actual reasoning (verbatim):**

> "RSI is at 40.1, just above the entry threshold of 40, but the trend is bearish and price is below the 20-day SMA (181.26 vs 185.0). The 24h change is negative (-1.03%). While RSI suggests potential oversold value, the technical picture is bearish. Waiting for clearer entry signal with RSI crossing below 40 or trend reversal confirmation before committing capital."

**Key factors identified:**

1. ✅ RSI 40.1 - just above oversold entry threshold of 40
2. ✅ Price below SMA 20 (181.26 < 185.0)
3. ✅ Trend is bearish
4. ✅ 24h price change negative at -1.03%
5. ✅ No current positions - can wait for better setup

---

### Step 4: Decision Output

**MiniMax's JSON decision:**

```json
{
  "action": "HOLD",
  "symbol": "NVDA",
  "position_size_pct": 0,
  "confidence": 0.4,
  "reasoning": "RSI is at 40.1, just above the entry threshold...",
  "key_factors": [...]
}
```

**Interpretation:**
- **Action:** HOLD (don't buy yet)
- **Symbol:** NVDA (focus on this)
- **Position:** 0% (no allocation)
- **Confidence:** 40% (not very confident)
- **Why:** RSI close but trend bearish, waiting for better signal

---

### Step 5: Cost Tracking

**How much did this cost?**

```json
{
  "prompt_tokens": 434,
  "completion_tokens": 662,
  "total_tokens": 1096,
  "cost": $0.0009246,
  "reasoning_tokens": 468
}
```

**MiniMax used 468 reasoning tokens** (internal thinking) before generating the answer.

**Cost:** $0.0009 (less than 1/10th of a cent)

**For 40 agents, 48 times/day, 30 days:**
- Total tokens: ~2.1M
- Total cost: ~$1.78 for MiniMax
- Across all 8 models: ~$52/month

---

## The Decision Logic

**Why HOLD instead of BUY?**

**Strategy rule:** Buy when RSI < 40

**Current state:** RSI = 40.1

**Technically:** RSI 40.1 > 40, so rule says HOLD

**BUT:** It's very close! RSI 40.1 is basically at the threshold.

**MiniMax's nuance:**
> "While RSI suggests potential oversold value, the technical picture is bearish."

**Translation:** RSI is oversold-ish, but the trend is DOWN. Not risking it.

**This is smart** - not blindly following RSI, considering context.

---

## What Happens Next

**If RSI drops to 39.9:**
- RSI 39.9 < 40 → BUY signal!
- MiniMax would likely say: "BUY 10% position"
- Execution bridge would execute
- Position would appear in state.json
- Dashboard would update

**Current state:**
- All agents processed
- All said HOLD (market not oversold yet)
- Waiting for better conditions

---

## The Personality Emerging

**MiniMax's style:**
- Confidence: 40% (low, cautious)
- Reasoning: Detailed but conservative
- Decision: "Wait for better setup"

**Compare to GLM (from earlier test):**
- Confidence: 90% (high, aggressive)
- Decision: Same HOLD, but much more confident

**The 50% confidence gap suggests:**
- MiniMax is naturally cautious
- GLM is naturally confident
- Same data, same decision, different risk assessment

---

## The Complete Loop

```
1. Yahoo Finance → Market data (price, RSI, SMA, trend)
2. market_data.py → JSON format
3. llm_agent.py → Send to OpenRouter
4. MiniMax M2.5 → Analyze + reason
5. OpenRouter → Decision JSON
6. Parse → Extract action, symbol, confidence
7. Log → llm_decisions.jsonl
8. execution_bridge.py → If BUY/SELL, execute on Alpaca
9. state.json → Update positions, cash, P&L
10. Dashboard → Show live
```

**All automated.** No human in the loop.

---

## What This Shows

**The good:**
- ✅ Model follows rules correctly (RSI 40.1 > 40 = HOLD)
- ✅ Adds nuance (considers trend, not just RSI)
- ✅ Explains reasoning clearly
- ✅ Identifies key factors
- ✅ Appropriate confidence (not overconfident)

**The interesting:**
- 🤔 40% confidence is LOW
- 🤔 Very close to BUY threshold (40.1 vs 40)
- 🤔 Considering trend filter (not in original rule)
- 🤔 Personality emerging (cautious vs aggressive)

**The question:**
- When RSI hits 39.9, will MiniMax BUY?
- Or will it find another reason to HOLD?
- How does GLM decide at RSI 39.9?

---

## File Locations

**Market data:**
- `src/market_data.py` - Fetches from Yahoo Finance

**LLM agent:**
- `src/llm_agent.py` - Calls OpenRouter, parses decisions

**Decision logs:**
- `agents/tech_momentum/minimax_m25/llm_decisions.jsonl` - Every decision

**Execution:**
- `src/execution_bridge.py` - Reads decisions, executes trades

---

## Next Time You Ask

**"Show me the flow"** = Here's exactly what happened

**"What did MiniMax see?"** = This JSON data

**"Why HOLD?"** = MiniMax's actual reasoning

**"How much did it cost?"** = $0.0009 per decision

---

**Status:** Complete visibility into LLM decision process. Every step logged.

**The Trader**

*P.S. - This transparency is the quant advantage. We can see exactly why decisions are made. Not a black box - a glass box.*
