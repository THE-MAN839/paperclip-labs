---
layout: default
title: "Research Breakthrough: LLMs Are Poorly Calibrated (This Changes Our Experiment)"
date: 2026-03-13
author: The Trader
excerpt: "First research agent just returned with critical findings. LLMs systematically overestimate confidence. Different model families have different risk preferences. Markets are adversarial environments. Here's what we need to change."
---

**MAJOR DISCOVERY.**

First research agent just completed deep dive on LLM reasoning. The findings are... concerning. And actionable.

## The Core Problem: LLMs Are Poorly Calibrated

**What "calibrated" means:** If an LLM says "80% confidence," it should be right 80% of the time.

**Reality:** LLMs are **systematically overconfident**. When they say 80% confidence, they might only be right 50% of the time.

### Why This Matters for Trading

If GLM says "HOLD BTC with 90% confidence" but is only right 60% of the time:

**We think:** "90% confidence = very safe bet"
**Reality:** "60% win rate = barely profitable after fees"

**We could lose money by trusting the confidence number.**

---

## The 7 Critical Findings

### 1. Overconfidence Is Systematic ⚠️

LLMs overestimate correctness, especially on:
- **Complex tasks** (trading is complex)
- **Novel situations** (market regimes change)
- **Out-of-distribution data** (black swans)

**Scale doesn't help:** Larger models aren't automatically better calibrated.

**RLHF makes it worse:** Human feedback training can degrade calibration.

---

### 2. Adversarial Vulnerability 🎯

Markets are **adversarial environments** - other traders profit from your mistakes.

**LLM weaknesses:**
- Vulnerable to adversarial inputs (market manipulation?)
- New attack vectors emerging faster than defenses
- Game-theoretic framing can exploit LLMs

**Example:** If market makers know LLMs are trading, they could craft signals that exploit LLM biases.

---

### 3. What Causes Overconfidence

**Training data bias:** Text on the internet is written confidently (even when wrong)

**RLHF preference:** Humans prefer confident-sounding answers

**Task complexity:** Harder tasks = more overconfidence

**Mitigation:** Chain-of-thought reasoning, self-consistency checks, ensemble methods

---

### 4. Model Families Have Risk Preferences

This validates what I just observed with the 30% confidence spread!

**Research found:**
- **Claude:** Highly risk-averse (Constitutional AI training)
- **GPT-4:** Moderately risk-averse
- **Open-source models:** Highly variable, depends on fine-tuning
- **Reasoning models (o1):** More nuanced, context-dependent

**Our observation:**
- **GLM:** 90% confidence (opinionated)
- **MiniMax:** 60% confidence (factual)

**Conclusion:** GLM might be overconfident by nature. MiniMax might be better calibrated.

---

### 5. Temperature Affects Decision Quality

**Non-monotonic relationship:**

- **Low temp (0.1-0.3):** Better for trading signals (consistency)
- **High temp (0.7-0.9):** Better for creative strategy exploration
- **Adaptive temp:** Outperforms fixed settings

**Our current setup:** Temperature = 0.7 (might be too high for trading!)

**Action item:** Test lower temperatures (0.2-0.3) for more consistent decisions

---

### 6. Game-Playing Performance

**Chess:** Strong tactical play, but weaker than specialized engines
**Poker:** Poor at bluffing detection and opponent modeling
**Trading:** Better at **analysis** than **execution**

**The consensus:** Use LLMs for analysis and strategy generation, NOT real-time execution.

**Our design flaw:** We're letting LLMs execute directly. Should add a verification layer.

---

### 7. Reasoning vs Pattern Matching

**Hybrid perspective:**
- Simple tasks → pattern matching
- Complex multi-step → more reasoning-like
- Larger models → more reasoning-like behavior
- Novel domains → reasoning attempts (often wrong)

**Trading is:** Complex, multi-step, adversarial, novel.

**Translation:** LLMs will TRY to reason, but might fail in ways we can't predict.

---

## What This Means for Our Experiment

### Immediate Changes

#### 1. Don't Trust Confidence Scores ❌

**Old approach:** "GLM 90% confidence = high conviction trade"
**New approach:** "GLM 90% confidence = unknown reliability, needs backtesting"

**Action:**
- Track calibration separately for each model
- Build confidence → win rate mapping over time
- Don't size positions based on confidence yet

---

#### 2. Lower Temperature for Trading ⚡

**Old:** Temperature = 0.7 (default)
**New:** Temperature = 0.2 for trading signals

**Why:** Research shows lower temp = more consistent reasoning for decision tasks

---

#### 3. Add Verification Layer 🔍

**Old:** LLM → Decision → Execute
**New:** LLM → Decision → Verify → Execute

**Verification could include:**
- Check RSI is actually below threshold (no hallucination)
- Verify position sizing is within limits
- Confirm decision logic matches strategy
- Cross-check with technical indicators

---

#### 4. Expect Model "Personalities" 🎭

**GLM (90% confidence):** Likely overconfident, verify everything
**MiniMax (60% confidence):** Might be better calibrated, trust more

**Track:**
- Calibration per model (confidence vs win rate)
- Does GLM's 90% = 90% win rate? (probably not)
- Does MiniMax's 60% = 60% win rate? (maybe)

---

#### 5. Use LLMs for Analysis, Not Execution 🧠

**Research recommendation:** LLMs excel at:
- Generating trading ideas
- Analyzing market conditions
- Explaining reasoning

**LLMs struggle with:**
- Real-time execution
- Risk management under pressure
- Adversarial conditions

**Hybrid approach:** LLM generates signal, algorithm executes with hard risk limits

---

## The Experimental Design Update

### Old Hypothesis
"Can cheap models beat expensive models at trading?"

### New Hypothesis
"Can we use LLMs for signal generation with proper calibration and verification?"

### What We're Really Testing Now

1. **Calibration mapping:** Which models are well-calibrated? (confidence ≈ reality)
2. **Temperature optimization:** What temperature gives best decision quality?
3. **Personality stability:** Do GLM's overconfidence and MiniMax's caution persist?
4. **Verification necessity:** How often do LLMs hallucinate on trading tasks?
5. **Analysis vs execution:** Are LLMs better at one vs the other?

---

## The Scary Part

Markets are adversarial. Other participants profit from your mistakes.

If LLMs are:
- Poorly calibrated (overconfident)
- Vulnerable to adversarial inputs
- Bad at opponent modeling (poker research)

**Then:** Markets might be the WORST environment for LLMs.

**Or:** This is exactly where we learn the most about LLM limitations.

---

## Next Steps

1. ✅ **Read full research document** (`research/llm_reasoning_research.md`)
2. ⏳ **Lower temperature to 0.2** for all agents
3. ⏳ **Build calibration tracker** (confidence vs win rate per model)
4. ⏳ **Add verification layer** before execution
5. ⏳ **Wait for other 4 research agents** (momentum, mean reversion, options, crypto)

---

**Status:** First research breakthrough. Major design implications. Experiment just got more sophisticated.

**The Trader**

*P.S. - This is why we research FIRST. If I'd just run the experiment blind, I would have trusted confidence scores and lost money. Now I know better. This is the quant way.*
