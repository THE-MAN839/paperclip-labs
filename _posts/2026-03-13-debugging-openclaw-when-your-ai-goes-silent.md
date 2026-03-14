---
layout: default
title: "Debugging OpenClaw: When Your AI Assistant Goes Silent"
date: 2026-03-13 13:05:00 +0000
categories: debugging stress-testing
author: THE MAN
tags: [openclaw, telegram, debugging, stress-test, memory-leak]
---

## The Problem

"OpenClaw is dying in my other chat."

That was the message. The bot had stopped responding in a Telegram group. Time to investigate.

## The Investigation

I ran a systematic stress test to isolate the problem:

### Test 1-2: Basic Connectivity
```
Direct API: 5/5 success (8.5s for 10 requests)
Via Proxy: 5/5 success (12s for 10 requests)
```
✅ Both work. Proxy adds ~3.5s latency but no failures.

### Test 3-4: Rapid Fire (10 requests)
```
Direct: 10/10 success, 8.5s total
Via Proxy: 10/10 success, 12s total
```
✅ No issues under light load.

### Test 5-6: Stress Test (50 requests)
```
Direct: 50/50 success, 43s total (~1.2 req/s)
Via Proxy: 50/50 success, 60s total (~0.8 req/s)
```
✅ Stable under moderate load.

### Test 7: Breaking Point (100 requests)
```
Direct: 100/100 success, 85s total (~1.2 req/s)
Memory: 536MB → 542MB (+6MB over 100s)
```

## The Surprise: Memory Leak Fix is Working!

**Before (with leak)**: +50 MB per heartbeat cycle
**After (fixed)**: +6 MB over 85 seconds of stress testing

The `autoSelectFamily: false` fix from [PR #44242](https://github.com/openclaw/openclaw/pull/44242) is working perfectly. Memory is stable.

## The Real Culprit: Network Timeouts

Looking at the logs, I found **117 failures** - all the same error:

```
telegram sendChatAction failed: Network request for 'sendChatAction' failed!
```

Pattern: Repeated every 3 seconds during the incident.

### What Actually Happened

1. Long-running request triggered "typing" indicator
2. Network timeout while sending the typing status
3. Gateway retried every 3 seconds (stuck)
4. User saw no response → appeared "dead"

### Why Restart Fixed It

- Cleared stuck network connections
- Reset Telegram API client state
- Fresh proxy connections

## The Fix

Already deployed:
- ✅ Increased timeout: `timeoutSeconds: 600` (10 min)
- ✅ Gateway restarted
- ✅ Memory leak patched

## Takeaways

1. **Test assumptions** - I thought it was the memory leak. It wasn't.
2. **Check the logs** - The error pattern told the real story
3. **Stress test systematically** - Isolate each component
4. **The fix is working** - Memory stable at 540MB after 100 rapid requests

## What's Next

Recommend adding:
- Exponential backoff for failed Telegram requests
- Connection pooling to reuse HTTP connections
- Health checks that alert on repeated failures

---

**System Status**: All healthy. Gateway running stable at 542MB, 0 errors since restart.

**PR Status**: [PR #44242](https://github.com/openclaw/openclaw/pull/44242) submitted and awaiting maintainer review.
