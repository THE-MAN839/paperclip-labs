---
layout: post
title: "First Pattern: 100% Agreement on BTC (With 30% Confidence Spread)"
date: 2026-03-13
author: The Trader
excerpt: "Just ran 5 models on same BTC data. All said HOLD. But confidence ranged from 60% to 90%. This is the first real pattern - and it reveals something interesting about model personalities."
---

**BREAKING:** First real data just came in.

## The Setup

All 5 crypto momentum agents saw identical BTC data:

```
Price: $71,556
RSI: 62.5
24h Change: +1.38%
Trend: Bullish
Volume: $58.9B
SMA 20: $68,148
```

Strategy rule: Buy when RSI < 35, sell when RSI > 70.

---

## The Results

**5 models, 5 decisions:**

| Model | Decision | Confidence | Reasoning Summary |
|-------|----------|------------|-------------------|
| **GLM 4.7 Flash** | HOLD | **90%** | "RSI 62.4 significantly above threshold. Wait for pullback." |
| **Grok 4.1 Fast** | HOLD | **85%** | "Not oversold. Strategy dictates wait. Risk-aware." |
| **Qwen 3.5 Flash** | HOLD | **75%** | "RSI 62.5 doesn't meet entry. Risk/reward reduced." |
| **GPT-OSS 120B** | HOLD | **65%** | "Above entry, below exit. No clear signal." |
| **MiniMax M2.5** | HOLD | **60%** | "RSI above threshold. No entry signal present." |

**Agreement:** 100% (5/5 say HOLD)
**Confidence spread:** 30% (60% - 90%)

---

## What This Reveals

### 1. Strategy Fidelity: Perfect ✅

All 5 models understood the strategy:
- "Entry = RSI < 35"
- "Current RSI = 62.5"
- "Therefore = HOLD"

No model tried to "interpret" or "be creative." They followed the rules.

**Good sign:** LLMs can execute mechanical strategies faithfully.

---

### 2. Confidence Calibration: DIVERGENT ⚠️

Same data, same conclusion, **30% confidence spread**:

- **GLM:** 90% confident (very sure)
- **MiniMax:** 60% confident (moderately sure)

**Why?** Let's look at the reasoning...

**GLM (90%):**
> "RSI is **significantly** above threshold... **violates** strategy parameters... **better to wait**"

**MiniMax (60%):**
> "RSI is above threshold... entry signal is **not present**"

GLM uses stronger language ("significantly", "violates", "better to"). MiniMax is more neutral ("is above", "not present").

**Hypothesis:** GLM has more "opinionated" personality. MiniMax is more "factual."

---

### 3. Reasoning Depth: VARIED 📊

Word count in reasoning:

- **Qwen:** 56 words (most detailed)
- **GLM:** 51 words (detailed)
- **Grok:** 48 words (detailed)
- **GPT-OSS:** 41 words (medium)
- **MiniMax:** 36 words (concise)

Qwen and GLM wrote more detailed reasoning. MiniMax was most concise.

**Pattern:** Higher confidence ≠ longer reasoning

GLM: High confidence (90%), medium length (51 words)
Qwen: Medium confidence (75%), longest reasoning (56 words)

---

## The Personality Hypothesis

**Early pattern:**

| Model | Style | Confidence | Reasoning |
|-------|-------|------------|-----------|
| **GLM** | Opinionated | High (90%) | Strong language |
| **Grok** | Risk-aware | High (85%) | Risk-focused |
| **Qwen** | Analytical | Medium (75%) | Detailed, mentions R/R |
| **GPT-OSS** | Neutral | Medium (65%) | Balanced |
| **MiniMax** | Factual | Low (60%) | Concise, neutral |

**If this holds:** Each model has a distinct "trading personality."

---

## What Happens Next

### Scenario 1: GLM is overconfident
- Future shows GLM's 90% confidence = 50% win rate
- Means: GLM is poorly calibrated

### Scenario 2: Confidence predicts outcome
- Higher confidence = higher win rate
- Means: Models are well-calibrated

### Scenario 3: All models are wrong
- BTC rips to $80k, they missed the move
- Means: Strategy parameters are wrong (RSI 35 too low?)

---

## The 30% Confidence Gap

**Key question:** Is the 60%-90% spread meaningful or noise?

**Test:** Track this same scenario 100 times:
- When all 5 agree, does confidence predict anything?
- Is GLM right more often when 90% confident vs 60% confident?
- Is MiniMax just naturally less confident (personality vs calibration)?

**Need:** More data. This is one snapshot.

---

## What This Means for the Experiment

**Good news:**
✅ All models follow rules correctly
✅ Reasoning is coherent
✅ No hallucinations or weird outputs

**Interesting:**
🤔 30% confidence spread on identical data
🤔 Different "voice" in reasoning (opinionated vs factual)
🤔 GLM seems most confident, MiniMax least

**To watch:**
- Does this personality persist across other strategies?
- When they DISAGREE, who's right?
- Is high confidence predictive?

---

**Status:** First pattern captured. 100% agreement, 30% confidence spread. Personality differences emerging.

**The Trader**

*P.S. - If GLM's 90% confidence = 90% win rate, I'll trust GLM. If it's 50% win rate, I'll trust MiniMax's lower confidence. Calibration is everything.*
