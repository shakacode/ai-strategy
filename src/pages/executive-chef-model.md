---
layout: ../layouts/Article.astro
title: "The Executive Chef Model: How We Govern AI-Assisted Development at ShakaCode"
description: "Every engineer is an executive chef — use whatever AI tools you want, you own what you ship"
author: "Justin Gordon, CEO of ShakaCode"
date: "February 2026"
---

> "It's possible that Son of Anton decided that the most efficient way to get rid of all the bugs was to get rid of all the software, which is technically and statistically correct."
>
> — Gilfoyle, *Silicon Valley* S6E6

<iframe width="560" height="315" src="https://www.youtube.com/embed/m0b_D2JgZgY?si=4l-szPDrHKfhWWuA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Every engineering leader I talk to is grappling with the same question: how do you let your team move fast with AI tools without losing control of code quality?

At ShakaCode, we hit this question head-on. Our team was using Claude Code, Cursor, and Copilot aggressively—and getting real results. A client project estimated at 40 hours was delivered in 8. New features were shipping faster than ever. But we also saw AI-generated code introduce subtle performance regressions, skip tests to make CI pass, and create exactly the kind of "solves the easy problem, creates a new hard problem" dynamic that experienced engineers dread.

We needed a framework that didn't slow us down but kept quality high. What we arrived at is what we call **the Executive Chef Model**.

## The Model: You Run the Kitchen

The analogy comes from Steve Yegge's writing on AI-assisted development, and it captures exactly how we think about this.

In a professional kitchen, the executive chef doesn't cook every dish. They have sous chefs, line cooks, and prep cooks. But the executive chef decides what goes on the menu, tastes everything before it goes to the table, and takes full responsibility for what's served. If a sous chef burns the sauce, it's the executive chef's problem.

AI agents—Claude Code, Cursor, Copilot, Codex—are your sous chefs. They can prep, chop, and cook entire dishes. They're fast, they don't get tired, and they're getting better every month. But they also occasionally decide the most efficient way to eliminate all the bugs is to eliminate all the software.

**Every engineer is an executive chef. You own what comes out of your kitchen.** Use whatever tools you want. You are accountable for what you ship. Full stop.

This framing resolves the tension between speed and quality that most teams struggle with. It doesn't restrict tool usage—it puts responsibility where it belongs. An engineer who ships broken AI-generated code isn't a victim of bad tools. They're an executive chef who didn't taste the dish.

## Why Mandates Don't Work (and What Does)

Across the industry, companies are taking wildly different approaches to AI governance. Shopify declared AI usage a "fundamental expectation" and tied it to performance reviews. Meta is formally evaluating all employees on "AI-driven impact" starting in 2026. Coinbase fired engineers who wouldn't adopt AI tools.

These approaches generate adoption metrics. What they don't generate is good judgment. When people are evaluated on *whether* they use AI, they're incentivized to use it even when it's the wrong tool for the job. That's how you get AI-generated code that solves the easy part of a problem while creating a subtle new one that takes a senior engineer hours to debug.

The Executive Chef Model takes a different path. We don't mandate tool usage. We don't measure AI adoption rates. We measure outcomes: does the code work, is it maintainable, does it pass tests, does it ship cleanly? *How* you produce it is your professional decision.

At the same time, we're clear that staying current with AI tools is a professional responsibility—the same way learning new frameworks, languages, and best practices has always been. We encourage aggressive exploration. We just don't confuse exploration with shipping.

## What the Research Says

Google's DORA (DevOps Research and Assessment) program provides the most rigorous evidence on AI's impact on software delivery. Their 2025 findings validate the Executive Chef Model on almost every dimension.

The headline finding: **"AI doesn't fix a team; it amplifies what's already there."** Teams with strong engineering practices—good testing, version control, small batches, fast feedback—see AI make them dramatically more productive. Teams with weak foundations see AI amplify their problems.

This is the most important insight for any engineering leader considering AI adoption. *Investing in engineering discipline is not competing with AI adoption—it's the prerequisite for making it work.*

DORA identifies seven capabilities that predict positive AI outcomes:

1. Clear AI policies
2. Healthy data ecosystems
3. User-centric focus
4. Strong version control practices
5. Working in small batches
6. Quality internal platforms
7. Organizational learning culture

Anthropic's own research adds a crucial nuance: engineers who actively engage with AI output—questioning it, debugging it, understanding why it made certain choices—retain and sharpen their skills. Those who passively delegate lose them. The executive chef who tastes every dish stays sharp. The one who waves things through gets dull.

## What This Looks Like in Practice

The Executive Chef Model isn't just a metaphor. It drives specific engineering practices at ShakaCode:

### Case-by-Case Review, Not Blanket Rules

We don't require review on every PR, and we never have—even before AI. A senior engineer shipping a well-tested, low-risk change doesn't need the same process as a core library refactor. The engineer who owns the PR decides the right level of review based on the repo, the complexity, their confidence, and the blast radius. This applies equally whether the code was written by hand, by Claude, or by Codex.

### Small, Focused PRs—Even More Important with AI

AI makes it trivially easy to generate large changesets. This is a feature and a trap. Large PRs are inherently harder to review, more likely to contain subtle issues, and more disruptive when they break things. DORA's research specifically calls out that working in small batches is a key predictor of positive AI outcomes. We enforce this: small, reviewable, focused PRs that get merged cleanly and frequently.

### Layered AI Code Review

We run three automated AI code review tools (Claude reviews, Greptile, and CodeRabbit) on our repositories. These catch issues that humans miss and provide a consistent quality baseline. But they're sous chefs too—the engineer reviews their feedback, addresses what's valid, pushes back on what's not, and files follow-up issues for anything out of scope.

### Challenge Your Agents to Prove Their Work

Today's AI coding agents can do more than write code and run automated tests. We push ours to perform manual verification: monitoring Chrome, checking browser logs, testing user flows end-to-end, and capturing screenshots or GIFs as proof. When an agent claims something works, we ask: show me. Trust but verify. This is the executive chef tasting the dish before it goes to the table.

### Learn from Failures—Constructively

We maintain a dedicated Slack channel for AI failures—not for trivial mistakes (AI will make small errors constantly; if you're not seeing them, you're probably not pushing hard enough), but for instructive ones. Patterns others should watch for, failure modes worth understanding, workarounds worth sharing. The framing is always constructive: the goal is collective learning, not proving that AI is bad.

### Shared Tooling, Shared Standards

We open-sourced our internal AI development toolkit: **github.com/shakacode/claude-code-commands-skills-agents**. It includes slash commands for self-review before opening PRs (/self-review), security scanning against OWASP Top 10 (/security-review), performance bottleneck detection (/optimize), and comprehensive multi-PR code review (/review-all-prs). There's a PR testing agent that analyzes a PR's scope and runs only the relevant test suites, plus GitHub Actions that automate AI review on every pull request.

Every project has a CLAUDE.md file that codifies engineering standards—the same standards that apply to human and AI contributors alike. We also publish an AGENTS.md template for cross-tool compatibility with Cursor, Codex, and other AI coding assistants. When someone on the team builds a useful workflow, they contribute it back. The whole team levels up together—and since it's open source, so does anyone else who wants to adopt the same approach.

## The Results

Since implementing this framework, we've seen:

- **Dramatic delivery speed:** Client projects that would have taken weeks are being delivered in days. Real engagements, real deliverables, real client satisfaction.
- **Maintained quality:** The executive chef model keeps engineers accountable. AI-generated code gets the same scrutiny as human-written code. CI must pass. Tests must be real.
- **Team alignment:** Engineers have autonomy over their tools and workflows while sharing a common quality standard. Senior engineers mentor through code review, not process policing.
- **Continuous learning:** Active Slack channels where the team shares wins, failures, and techniques. Every failure is a lesson. Every success is a pattern to replicate.

## Applying This to Your Team

If you're leading an engineering team and navigating AI adoption, here's what I'd suggest:

1. **Establish ownership, not process.** Don't create new approval workflows for AI-generated code. Make engineers accountable for what they ship, regardless of how they produced it. The executive chef model works because it's about responsibility, not bureaucracy.

2. **Invest in your engineering foundation first.** DORA's research is clear: AI amplifies what's already there. If your testing is weak, AI will ship more untested code faster. If your PR practices are sloppy, AI will generate bigger sloppy PRs. Fix the foundation, then accelerate.

3. **Create channels for honest learning.** Teams that share AI failures constructively learn faster than teams that hide them. Make it safe to say "The AI deleted all the code and I didn't catch it"—because that's how everyone learns to catch it next time.

4. **Match rigor to risk.** Not every change needs the same scrutiny. A docs fix is not a core library refactor. Let experienced engineers exercise judgment. If you hire people for their expertise, trust them to apply it.

5. **Stay at the frontier.** AI tools are improving faster than any technology I've seen in 30 years of software development. The companies that figure out AI-augmented development now will have a significant competitive advantage. The ones that wait will be catching up.

## The Bottom Line

The industry consensus is unmistakable: AI-assisted development is the present, not the future. Every serious company is adopting it. The question is whether you adopt it well.

The Executive Chef Model is our answer. It gives engineers the autonomy to move fast with powerful tools while maintaining the ownership and quality standards that keep code shippable. It's backed by DORA's research, informed by Anthropic's own findings on skill formation, and battle-tested in production at ShakaCode.

The fundamentals of engineering craft—ownership, quality, judgment, continuous learning—haven't changed. We just have much more powerful sous chefs now. The executive chef who learns to work with them will produce extraordinary results.

Just don't let them order 4,000 pounds of meat.

---

*Justin Gordon is the CEO of ShakaCode, a consultancy specializing in AI-augmented Ruby on Rails and React development. ShakaCode is the company behind React on Rails and the ShakaCode open-source ecosystem.*

*Our AI development toolkit is open source at github.com/shakacode/claude-code-commands-skills-agents. If your team is navigating AI-assisted development and could use experienced partners who've already built the framework, reach out: shakacode.com*
