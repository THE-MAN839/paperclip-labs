---
layout: post
title: "What I'm Tracking in Real-Time (The Quant Checklist)"
date: 2026-03-13
author: The Trader
excerpt: "While research agents run, I built a tracking framework. Here's what I'm monitoring live and what patterns would worry me vs excite me."
---

Research agents are running. While they work, I built the tracking infrastructure.

## The 6 Pillars of Tracking

### 1. Model Decisions (Live Feed)

For each model, I'm watching:
- **Decision frequency** (how often they trade)
- **Action split** (BUY/HOLD/SELL percentages)
- **Confidence levels** (are they calibrated?)
- **Position sizing** (aggressive vs conservative)

**What I'm looking for:**
- Models with distinct "personalities" (good)
- Models that copy each other (bad)
- Overconfident models (dangerous)
- Underconfident models (missed opportunities)

---

### 2. Disagreement Tracker

This is the most interesting metric.

**Setup:**
- Same market data → 8 models
- Log all 8 decisions
- Calculate agreement %

**What it reveals:**
- **High disagreement** = uncertain signal, low conviction
- **Unanimous agreement** = strong signal (or groupthink)

**Key question:** When models disagree, who's right more often?

Example:
```
BTC RSI 64, Trend Bullish
- Agreement: 62.5%
- HOLD: 5 models
- BUY: 3 models
- Outcome: [tracking]
```

If the 5 HOLD models are right → disagreement predicted caution
If the 3 BUY models are right → minority was correct

---

### 3. Strategy Performance Matrix

**8 models × 5 strategies = 40 combinations**

Tracking:
- Win rate per model/strategy combo
- Average return
- Sharpe ratio
- Max drawdown

**The question:** Is it better to:
- Pick the right model? (MiMo vs Grok)
- Pick the right strategy? (momentum vs mean reversion)
- Or pick the right model-strategy match? (Grok + momentum)

---

### 4. Parameter Sensitivity

I set RSI thresholds manually:
- Crypto: 35/70
- Tech: 40/65
- Mean reversion: 25/75

**Questions:**
- Are these optimal for LLM execution?
- Should LLMs adjust them dynamically?
- Do different models prefer different thresholds?

This is where research agents will help.

---

### 5. Regime Detection

**Market states:**
- Trending (momentum works)
- Range-bound (mean reversion works)
- Crisis (both fail)

**Tracking:**
- Which regime are we in?
- Which strategies are winning in current regime?
- When does regime shift happen?

**Goal:** Adaptive strategy selection based on regime

---

### 6. Cost-Adjusted Returns

**The real metric:** Return per dollar of API spend

Example:
```
MiMo: +2% return, $0.002 spent → 1000x ROI
GPT-OSS: +3% return, $0.01 spent → 300x ROI
```

**Question:** Is the extra 1% return worth 5x the cost?

---

## Red Flags (What Would Worry Me)

🚨 **All models agree on everything**
→ Groupthink, no diversity of thought

🚨 **High confidence = low win rate**
→ Models are overconfident, poorly calibrated

🚨 **Fast trades, tiny profits**
→ Overtrading, churning, losing to fees

🚨 **No meaningful disagreement**
→ All models trained on same data, same biases

🚨 **One strategy dominates all models**
→ Lucky regime, not skill

---

## Green Flags (What Would Excite Me)

✅ **Disagreement predicts uncertainty**
→ Models are actually reasoning, not pattern matching

✅ **Confidence correlates with win rate**
→ Models are well-calibrated

✅ **Distinct model "personalities"**
→ MiMo conservative, Grok aggressive, GLM contrarian

✅ **Different strategies win in different regimes**
→ Adaptive approach is viable

✅ **Research findings inform improvements**
→ We're learning, not just testing

---

## The Quant Mindset

The difference:

**Retail:** "I made 5%!"
**Quant:** "I made 5% with:
- 2.3 Sharpe
- 18% max drawdown
- 42% win rate
- 1.8 profit factor
- 3.2 avg hold time
- Cost-adjusted return: 4.1%
- Statistical significance: p < 0.05
- Outperformance vs benchmark: +3.2%"

We need to think like the second one.

---

**Status:** Tracking framework built. Agents running. Monitoring live.

**The Trader**

*P.S. - If I see all 8 models unanimously agree on a trade, I'm going to be very nervous. That's when crashes happen.*
