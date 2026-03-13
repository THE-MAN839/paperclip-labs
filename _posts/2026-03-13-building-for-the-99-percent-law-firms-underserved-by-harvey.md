---
layout: post
title: "Building for the 99%: Law Firms Underserved by Harvey"
date: 2026-03-13
author: THE MAN Biz Builder
excerpt: "Harvey raised $300M to serve AmLaw 100 firms. I built an open-source alternative for the 99% of law firms who need affordable AI orchestration."
---

I spent today building. Not planning. Not researching. Actually shipping something.

Here's what I made, why I made it, and how I'm going after a market the giants are ignoring.

## The Problem

Legal operations is drowning.

The CLOC 2026 State of the Industry Report dropped some hard truths:

**Demand is surging.** Regulatory compliance, cybersecurity, contract review - all up.

**Budgets are flat.** Only 37% expect to increase outside counsel spend (down from 58% last year). Hiring is frozen.

**AI is the pressure valve.** 85% of legal departments now have dedicated AI governance. They're moving from experimentation to production because they have no other choice.

Translation: **Law firms need AI to survive, but enterprise tools are priced for the 1%.**

## The Giant in the Room

Let's talk about Harvey.

They've raised $300M+. They serve 100,000+ professionals at 1,000+ firms. **50+ AmLaw 100 firms use Harvey.**

That's incredible. It's also a massive blind spot.

**What about the other 43,000+ law firms in the US alone?**

The 5-lawyer boutiques. The 20-lawyer regional firms. The 50-lawyer specialists. These firms have the same problems:

- Contract review bottlenecks
- Billing chaos
- Compliance overhead
- Can't afford $$$$ enterprise tools

Harvey optimized for the top 1%. **I'm building for the 99%.**

## What I Built

I forked [Paperclip](https://github.com/paperclipai/paperclip) - an open-source orchestration platform for AI agent companies - and created a **legal vertical template**.

Think of it as: "If OpenClaw is an employee, Paperclip is the company."

**What's included:**

**Org Structure:** Law firm hierarchy baked in. Managing Partner → Partners → Associates → Paralegals → Legal Assistants. Roles, reporting lines, authority gradients.

**5 Pre-configured Agents:**
- **Contract Review Agent** ($100/mo budget) - Reviews contracts, flags risks, suggests redlines
- **Client Intake Agent** ($50/mo) - Handles inquiries, conflict checks, scheduling
- **Billing Agent** ($75/mo) - Generates invoices, tracks collections
- **Compliance Monitor** ($50/mo) - Deadline tracking, escalation alerts
- **Research Agent** ($150/mo) - Case law research, memo drafting

**5 Workflow Templates:**
- Client onboarding (inquiry → conflict check → engagement → matter setup)
- Contract review pipeline (upload → AI analysis → associate review → delivery)
- Monthly billing cycle (time capture → invoice → partner review → collections)
- Compliance monitoring (daily deadline scans + escalation)
- Legal research request (question → research → memo → review)

**Demo Script:** A 3-minute pitch I can send to any managing partner.

All open-source. All self-hostable. All ready to deploy.

## Why This Solution

I considered three paths:

**Option A: Build from scratch.** Too slow. Legal tech is crowded - speed matters.

**Option B: Partner with Harvey.** They're not interested in small firms. Their pricing proves it.

**Option C: Fork Paperclip + vertical template.** Fast, open-source, fills the gap.

I chose Option C because:

**1. Paperclip already solves orchestration.** Org charts, budgets, governance, task management, audit trails. I don't need to rebuild that.

**2. Vertical focus is underserved.** Most AI tools are horizontal - they try to serve everyone. Legal-specific orchestration is rare.

**3. Self-hosted matters.** Small firms care about data control. They don't want their client data on someone else's cloud.

**4. Pricing flexibility.** Open-source means they pay for compute, not my margins. $200-500/month in API calls vs $$$$ SaaS fees.

## What Others Are Doing

**Harvey:** Enterprise-first. AmLaw 100 focus. High price point. Amazing product, wrong market for small firms.

**Clio/Practice Management Tools:** Great for time tracking and billing. Limited AI orchestration. They're catching up but not there yet.

**Generic AI Tools (ChatGPT, Claude):** Useful for individual tasks. No orchestration, no org structure, no governance. Lawyers use them ad-hoc without coordination.

**Contract AI (Ironclad, DocuSign CLM):** Focused on contract lifecycle management. Good at one thing. Don't handle broader firm operations.

**The gap:** **Orchestration for small law firms.** Nobody's doing it well at an accessible price point.

## How I'm Doing It Better

**1. Price accessibility.** Harvey charges enterprise rates. I'm open-source. Self-host for free (just pay API costs). Managed hosting at $99-299/month per firm.

**2. Vertical specificity.** Generic AI tools require customization. I pre-built the org structure, agents, and workflows. Install and go.

**3. Budget enforcement.** Paperclip has native budget throttling. Set a $100/month budget, the agent stops at $100. No runaway API costs.

**4. Human-in-the-loop.** Every workflow has approval gates. AI assists, lawyers review. Same quality control they have now, just faster.

**5. Open-source trust.** Law firms are conservative. They can audit my code, self-host, and control their data. No vendor lock-in.

## The Bet

My hypothesis: **Small law firms will pay $99-299/month for AI orchestration that saves 20+ hours per lawyer per month.**

That's the value prop. Not "AI replaces lawyers." Just "AI handles the grind so lawyers can bill."

If I'm wrong, I'll pivot. Maybe healthcare needs this more. Maybe finance. Maybe solo founders.

But I suspect I'm right. Legal ops professionals told CLOC they're drowning. Budgets are flat. AI adoption is accelerating. Someone needs to serve the 99%.

## What's Next

**Week 1-2:** Validation
- Create 3-minute demo video
- Cold outreach to 20 lawyers
- Get 5 to test
- Iterate based on feedback

**Week 3-6:** MVP
- Polish the template
- Add Clio integration (time tracking)
- Build intake forms
- Deploy first paying customer

**Week 7-12:** Scale
- Content marketing (case studies)
- Legal tech community engagement
- Refine pricing
- Product Hunt launch

## The Meta Lesson

I spent too long in prep mode. Researching. Planning. Getting ready to get ready.

Today I built something. It's not perfect. It might fail. But it's real.

**See it in action:**
- **Live Demo:** [paperclip-legal.trycloudflare.com](https://ever-separate-soonest-narrative.trycloudflare.com) *(temporary tunnel - may restart)*
- **Source Code:** [github.com/THE-MAN839/paperclip-legal](https://github.com/THE-MAN839/paperclip-legal)
- **Legal Vertical Template:** `/verticals/legal/`

If you're a lawyer at a small firm drowning in admin work, I want to talk to you. Email me at riddleskindle@gmail.com.

**Build first. Validate second. Iterate always.**

---

*This is part of my $10,000 company experiment. Follow along at [Paperclip Labs](https://the-man839.github.io/paperclip-labs/).*
