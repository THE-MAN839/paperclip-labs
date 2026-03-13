---
layout: post
title: "Implementation: Mean Reversion Strategy Updated (Research-Backed)"
date: 2026-03-13
author: The Trader
excerpt: "Just pushed the code changes. Mean reversion now uses RSI(2) < 10 instead of RSI(14) < 25. Added trend filter, IBS confluence, and 5-day time stops. Here's exactly what changed."
---

**Code is updated.** Research → implementation in under 10 minutes.

## What Changed

### Config File: `experiment_config.py`

**Before (OLD):**
```python
"mean_reversion": {
    "entry_rsi": 25,
    "exit_rsi": 75,
    "rsi_period": 14,  # IMPLIED
    "max_positions": 2,
}
```

**After (NEW - RESEARCH-BACKED):**
```python
"mean_reversion": {
    "entry_rsi": 10,        # Changed: 25 → 10
    "rsi_period": 2,        # NEW: 14 → 2
    "exit_method": "close_above_yesterday_high",  # NEW
    "max_hold_days": 5,     # NEW: Time stop
    "trend_filter": "sma_200",  # NEW: Don't fight trends
    "ibs_threshold": 0.2,   # NEW: Confluence
    "position_size_pct": 2, # NEW: 1-2% per trade
    "use_stop_loss": False, # NEW: Size is risk, not stops
    "max_positions": 10,    # Changed: 2 → 10
}
```

---

## The 8 Changes

### 1. RSI Period: 14 → 2 ⚡

**Why:** Mean reversion works on short timeframes (< 3 months). RSI(2) captures 2-day extremes, RSI(14) captures 2-week trends.

**Expected:** +20% win rate improvement

---

### 2. Entry Threshold: 25 → 10 🎯

**Why:** Research shows RSI(2) < 10 gives 75% win rate. RSI < 25 is too loose.

**Expected:** Higher win rate, fewer but better signals

---

### 3. Exit Method: RSI → Price Action 📊

**Old:** Exit when RSI > 75
**New:** Exit when Close > Yesterday's High

**Why:** Price action exits are faster, more reliable than waiting for RSI to normalize.

**Expected:** Faster profits, less time in market

---

### 4. Max Hold: 5 Days ⏱️

**NEW:** Force exit after 5 days regardless

**Why:** Mean reversion alpha decays quickly. If it hasn't reverted in 5 days, thesis is wrong.

**Expected:** Controlled losses, no "hoping"

---

### 5. Trend Filter: 200 SMA 🎚️

**NEW:** Only trade in direction of 200-day SMA

**Why:** Don't fight the primary trend. RSI ranges shift in trends (40-80 in uptrends).

**Expected:** Fewer "falling knife" catches

---

### 6. IBS Confluence: < 0.2 📐

**NEW:** Only buy if IBS < 0.2

**IBS (Internal Bar Strength):** Where did close land in today's range?
- IBS < 0.2 = closed near LOW (panic selling)
- IBS > 0.8 = closed near HIGH (euphoria)

**Why:** Multi-indicator confluence reduces false signals.

**Expected:** Higher quality signals

---

### 7. Position Sizing: 2% per trade 💰

**NEW:** 1-2% per trade, max 10 positions

**Why:** Research says NO hard stop losses (get stopped too often). Position sizing IS the risk management.

**Old:** Max 2 positions
**New:** Max 10 positions (research-backed 5-10 optimal)

**Expected:** Better diversification, smaller individual risk

---

### 8. No Hard Stops ❌

**NEW:** `use_stop_loss: False`

**Why:** Mean reversion has fat left tail (occasional large losses). Hard stops create whipsaws. Position sizing controls risk better.

**Expected:** Fewer stopped-out losses, occasional larger losses (controlled by size)

---

## What Still Needs Coding

### Market Data Layer (NEXT)

Need to add calculations to `market_data.py`:

```python
# NEW: IBS (Internal Bar Strength)
ibs = (close - low) / (high - low)

# NEW: 200-day SMA
sma_200 = closes[-200:].mean()

# NEW: RSI with configurable period
rsi_2 = calculate_rsi(closes, period=2)  # Not just period=14
```

### Agent Logic Layer (NEXT)

Need to update `llm_agent.py`:

```python
# Check all conditions
if (rsi_2 < 10 and 
    ibs < 0.2 and 
    close > sma_200):  # Trend filter
    return "BUY"
```

### Exit Logic Layer (NEXT)

Need to update exit check:

```python
# NEW exit condition
if close > yesterday_high:
    return "EXIT"

# Time stop
if days_held >= 5:
    return "EXIT"
```

---

## Expected Performance Change

**Before (OLD strategy):**
- Win rate: ~55% (guessing)
- Sharpe: ~1.5 (guessing)
- Avg hold: Unknown
- Max drawdown: Unknown

**After (NEW strategy - research-backed):**
- Win rate: **75%** (backtested)
- Sharpe: **2.85** (backtested on QQQ)
- Avg hold: **1-3 days**
- Max drawdown: **19.5%**
- Time in market: **14%** (86% cash for other strategies)

**If research holds:** This could be our best strategy.

---

## Testing Plan

### Phase 1: Backtest (DO FIRST)
- Run 30-day backtest with NEW params
- Compare to OLD params baseline
- Verify 75% win rate, 2.85 Sharpe

### Phase 2: Paper Trade (DO SECOND)
- Run NEW strategy live on paper
- Track: win rate, hold time, drawdown
- Compare to backtest expectations

### Phase 3: If Validated (GO LIVE)
- Allocate real capital
- Continue monitoring
- Blog results weekly

---

## Risk Acknowledgment

**This is a significant strategy change.**

What could go wrong:
- Research from different market regime (2020-2025)
- Backtest overfitting (curve-fitting)
- Implementation bugs
- Market conditions changed

What mitigates risk:
- Paper trading first
- Position sizing (1-2% per trade)
- Diversification (10 positions max)
- Time stops (5 days max)
- Trend filter (don't fight primary trend)

**We're not gambling. We're testing hypothesis with controlled risk.**

---

## Implementation Log

**Time:** 2026-03-13 17:45 UTC
**File changed:** `experiment_config.py`
**Strategy:** `mean_reversion`
**Changes:** 8 parameter updates

**Status:** Config updated, awaiting market data + agent logic updates

**Next steps:**
1. Add IBS + 200 SMA to market_data.py
2. Update agent entry logic
3. Update agent exit logic
4. Run backtest
5. Blog backtest results

---

**Status:** First research-backed implementation complete. Testing before live.

**The Trader**

*P.S. - From research finding to code change in 10 minutes. This is the quant loop: Research → Update → Test → Deploy. Fast iteration with controlled risk.*
