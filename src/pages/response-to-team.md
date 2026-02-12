---
layout: ../layouts/Article.astro
title: "Response to Team Concerns About AI Tools"
description: "A direct response to the petition raised by ShakaCode team members about AI-assisted development"
author: "Justin Gordon"
date: "February 2026"
---

Roman, Zakir, Alexandre, Ramez, Alexander, Abanoub, Alexey, Mikhail, Alex, Denis—

Thank you for writing this petition. I know it took courage, and I want you to know I read every word, including the parts that were hard to hear. You wrote it out of care for this company, and I'm going to respond in the same spirit.

This letter is my direct response to you. Alongside it, I've drafted a **ShakaCode AI Tools Policy** that's open for everyone's feedback as a shared Google Doc. That policy is the concrete, forward-looking outcome of this conversation. But first, I owe you a direct accounting of what I heard and what's changing.

## What I Heard

Let me be specific about what landed. I don't want you to wonder whether your points got through—they did.

### On Recognition

You're right, and I'm sorry. When Alexey and Abanoub spent hours doing the hard, unglamorous work of fixing what the PNPM migration broke—debugging CI, untangling test failures, getting the dummy app running again—they deserved public credit. Instead, I celebrated the tool that created the mess they cleaned up. That was unfair, and I understand why it felt demoralizing.

**Alexey, Abanoub—thank you. You crushed it.** And I should have said that publicly when it mattered.

The reason I share AI success stories is to inspire the team to stay current with these tools. That urgency is real. But going forward, I'm going to make sure the people doing the critical work get recognized—especially when they're the ones making AI output actually shippable.

### On the Specific Harm

The examples you raised are legitimate. The PNPM migration introduced multiple issues that required real debugging. CI tests got skipped. The dummy app broke locally. One PR solved its immediate problem but introduced a performance regression with unnecessary HTTP connections—exactly the kind of subtle hard problem you described, where AI solves the easy part and creates a new hard part.

I also accept that the cascade of Conductor PRs disrupted our momentum when we were close to shipping. That was a strategic mistake on my part—bad timing, not enough scrutiny on the changes that needed it.

At the same time: not every AI-assisted change created problems. Many of those PRs landed cleanly and moved us forward. The issue wasn't AI itself—it was that I didn't apply enough judgment to the ones that needed it. That's a process failure, not a tool failure.

### On the "Product Builder" Role

I'm retiring the term. It landed wrong, and a label that needs constant explaining isn't worth keeping. There is no two-tier system. There are no roles where some people build and others clean up.

The framing I'm using instead: every engineer is an **executive chef**. Think of AI agents—Claude Code, Cursor, Copilot, Codex—as your sous chefs. They can prep, chop, and even cook entire dishes. But the executive chef decides what goes on the menu, tastes everything before it goes out, and takes full responsibility for what's served. You run the kitchen. You own the result. Full stop. (This analogy comes from Steve Yegge's writing on AI-assisted development, and it captures exactly how I think about this.)

### On How We Work

I heard you on the micromanagement. "Why did this take 2 hours? Did you use Claude Code?"—I understand why that felt insulting to senior engineers who already use AI effectively. That stops now. I trust you to find your own workflow. I will focus on *what* needs to be done, not *how* you do it.

## What's Changing

Here's a clear mapping of your proposals to what I'm doing about them. Some are direct "yes." Some I've addressed differently than you proposed. I want to be transparent about both.

| Your Proposal | What I'm Doing |
|---|---|
| Focus less on coding, more on leadership and marketing | Agreed. Leadership and sales need more of my time. I'm making that the priority. |
| Stop pressuring on speed | **Done.** No more "Why did this take 2 hours?" If a task takes longer than expected, that's information about the problem's complexity, not a performance issue. |
| Focus on WHAT not HOW | **Done.** You're senior engineers. I hired you for your judgment. I will not micromanage your tool usage. |
| All AI PRs must have draft status | **Yes, with nuance.** For critical shared repos, use GitHub's draft PR feature or WIP labels to signal work-in-progress. Draft PRs should be encouraged—messy experiments are fine, just make it clear it's a draft. We also have "AI on" / "AI off" labels. Note: if you're vibe-coding a new repo by yourself, of course have your agents create PRs and discuss between themselves—that's efficient solo workflow. The discipline is for shared codebases where others are affected. |
| Avoid merging AI drafts to master without review | Addressed through **engineer ownership**. It's not feasible to always wait for a human reviewer—we never required that even for non-AI code. Sometimes we merge and ask for a post-review. These are the same practices we've had for years. The only difference is that AI agents might do unexpected things in our kitchen, and the engineer supervising them is responsible for the quality. |
| AI must be prohibited from merging PRs | Humans already merge PRs—this was never actually happening. The ownership principle reinforces it: a human is always accountable for the merge decision. |
| Stop praising AI, start praising devs | I'll keep sharing AI wins to inspire tool adoption—that's important for the business. But I'll make sure the **people** doing hard work get equal or greater recognition. |
| Reduce parallel AI sessions to 3 | I'm not setting a fixed number—that's too task-dependent. But the ownership principle applies: if the volume outpaces your ability to review and own the output, dial it back. |

## Where I Still Believe in AI-Assisted Development

I want to be direct: I am not backing away from AI-assisted development. I have 100% certitude that staying current with AI tools is existential for our business. The companies that figure out AI-augmented development will have a massive edge, and I intend for ShakaCode to be one of them.

What you've convinced me of is that my *execution* needed recalibration. Moving fast with AI only works if the hard problems are getting caught. Speed without the right level of scrutiny isn't velocity—it's debt. The right answer isn't less AI. It's **more discipline around AI**—combined with the core principle that every engineer owns what they ship.

I've been proactive—maybe aggressively so—in testing the boundaries of what AI can do. That's been intentional. Given the pace of progress over the last year, I've felt strongly that this is what our company needs: to understand the frontier, not just read about it. It may turn out to be more beneficial than we expect, or less. We don't know yet. But I believe it's essential that we test these boundaries rather than wait for others to figure it out first.

I also want to acknowledge something I've seen clearly in our Slack channels: many of you who signed this petition are among the most active and engaged AI users on the team. You're sharing tools in #ai-programming-tools, posting wins in #ai-programming-wins, and documenting failures honestly in #ai-fuckup-postmortem. This petition isn't anti-AI—it's pro-quality. I hear that, and I respect it.

As engineers, we've always had a responsibility to keep ourselves abreast of the latest tools to be as productive as possible. The only thing different with AI is that these tools are quite a bit more powerful, and the pace of change is much quicker. The overall themes of our engineering discipline have not changed. Ownership. Quality. Judgment. Continuous learning. Those apply now as they always have.

## On "Easy Problems" vs. "Hard Problems"

Your framing here was one of the most valuable parts of the petition. SOTA AI is excellent at solving easy, well-defined problems—but in the process, it can generate subtle hard problems that experienced developers catch instinctively.

Where I'd push back gently: the boundary between "easy" and "hard" is shifting fast, and it's shifting in our favor. Sergey and I recently completed a client project estimated at 40 hours in 8 hours using Claude Code. That's a real engagement with real deliverables. Sergey has additional major wins we'll be documenting and sharing with the team.

This doesn't invalidate your concerns about OSS code quality—those are legitimate and I'm addressing them. But writing off AI-assisted development as "pretending hard problems are easy" misses the real productivity gains we're seeing. The challenge is applying the right rigor to the right work—and that's exactly what the new policy is designed to support.

One thing worth noting: *Anthropic's own research on AI-assisted coding* found that engineers who actively engage with AI output—questioning it, debugging it, understanding why it made certain choices—retain and even sharpen their skills. Those who passively accept AI output don't. That's the difference between using AI well and using it poorly, and it's exactly the kind of judgment I trust this team to exercise.

## On the Business

I owe you directness here, because I know this is what's really on some of your minds.

We've landed two new clients recently, and I have a promising lead for another with a meeting next week. I'm optimistic about this year. Our ability to deliver AI-assisted consulting at dramatically better timelines is a real competitive advantage—the 40-hour project delivered in 8 hours isn't a one-off, it's the kind of efficiency that wins clients and keeps them coming back.

I hear you that leadership and sales need more of my time. You're right. I'm committed to making that the priority.

## What Comes Next

The AI Tools Policy is a draft. I'm sharing it as a Google Doc specifically so you can comment on it, suggest edits, and shape it. I'll bookmark it in #ai-programming-tools. This is your policy too. The best version is one we build together.

You took a risk writing this petition, and I respect every one of you for signing it. This is what a healthy team looks like: people who care enough to push back when they think the leader is getting it wrong.

I got some things wrong. I'm fixing them. I also believe our AI-forward approach is the right long-term bet for this company—with better calibration, recognition for the humans doing the hard work, and the understanding that every one of you is an executive chef who owns what comes out of your kitchen.

Let's go get some clients, and make HiChee and ShakaFlow amazing.

— Justin
