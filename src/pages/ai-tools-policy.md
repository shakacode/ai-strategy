---
layout: ../layouts/Article.astro
title: "ShakaCode AI Tools Policy"
description: "How ShakaCode governs AI-assisted development — the Executive Chef Model"
author: "Justin Gordon"
date: "February 2026"
---

> "It's possible that Son of Anton decided that the most efficient way to get rid of all the bugs was to get rid of all the software, which is technically and statistically correct."
>
> — Gilfoyle, *Silicon Valley* S6E6, after his AI also ordered 4,000 lbs of meat while looking for cheap hamburgers

## Purpose

If you've seen that clip, you laughed—and then you thought about it. AI tools are powerful, fast, and capable of impressive results. They can also do unexpected things if nobody's supervising. That's not a reason to stop using them. It's a reason to make sure the executive chef is always in the kitchen.

**The Executive Chef Model:** In an AI-augmented workflow, the engineer is the executive chef. AI agents—Claude Code, Cursor, Copilot, Codex—are your sous chefs. They can prep, chop, and even cook entire dishes. But the executive chef decides what goes on the menu, tastes everything before it goes out, and takes full responsibility for what's served. A sous chef might burn the sauce; the executive chef catches it. That's the model. You run the kitchen. (This analogy comes from Steve Yegge's writing on AI-assisted development, and it captures exactly how we think about this at ShakaCode.)

This document establishes ShakaCode's guidelines for using AI-assisted development tools. It reflects input from across the team and exists to give everyone a shared, clear framework. We want this to be a living document—your feedback is welcome and expected.

As engineers, we've always had a responsibility to stay abreast of the latest tools and to be as productive as possible. AI tools are no exception. What's different this time is the power and pace of change—but the core principles of our engineering discipline have not changed. We still own our work. We're still accountable for quality. We still use professional judgment about when and how to apply our tools.

## Core Principle: You Are the Executive Chef

Think of it like a kitchen: every engineer at ShakaCode is an executive chef. You are responsible for what comes out of your kitchen. Use whatever tools you want—AI assistants, code generators, pair programming, your own expertise. **You have final responsibility for what you serve.** Full stop.

This means there is no two-tier system. There are no roles where some people get credit for building and others clean up. Every engineer owns their output. How you produce it is your professional decision.

## Our Stance on AI Tools

AI-assisted development is a core part of how ShakaCode works and competes. Staying current with AI tools is not optional—it's a professional responsibility, the same way learning new frameworks, languages, and best practices has always been. The companies that figure out AI-augmented development will have a significant edge, and we intend to be among them.

At the same time, AI tools are exactly that—tools. They are powerful, they are improving rapidly, and they can produce impressive results. They can also introduce subtle bugs, miss context, and generate plausible-looking code that doesn't hold up under scrutiny. Experienced engineers catch these problems. That's why *human judgment remains the critical ingredient*.

Part of staying current means actively testing the boundaries of what these tools can do. We may not always get it right—some experiments will be more beneficial than we expect, some less. That's the nature of working at the frontier. What matters is that we're learning, sharing those lessons, and adjusting as we go. Companies like Shopify now treat effective AI usage as a baseline expectation for engineers. GitLab publishes evolving principles rather than rigid rules. Google's DORA research shows that disciplined AI adoption improves delivery—but only when paired with strong testing, review, and human oversight. We're following the same principle: adopt aggressively, govern thoughtfully.

We encourage every team member to explore, experiment with, and get comfortable with AI tools. Share what's working. Share what's not. The more we learn together, the better we all get.

## Guidelines for AI-Assisted Work

### 1. Engineer Ownership

Every engineer owns their pull requests. Whether you wrote the code by hand, used Claude Code, Cursor, Copilot, or any combination—the PR is yours. You own the quality. You own the decision about whether it needs review, and who that reviewer should be.

- **Technically complex or high-impact changes** should get experienced eyes on them.
- **Straightforward, well-understood changes** are your call—use your judgment.
- This applies equally whether the code was AI-assisted or not. A small docs fix from a senior engineer doesn't need the same process as a core library refactor.

### 2. Review Process: Case by Case

There is no one-size-fits-all review rule—and we've never had one, even for purely human-written code. Sometimes you request a review before merging. Sometimes you merge and ask for a post-review. Sometimes the change is straightforward enough that your own review is sufficient. These are the same practices we've followed for years. The only difference now is that we have AI agents working in our kitchen that might do unexpected things—and whoever is supervising them is the one responsible for ensuring the quality.

There's also a seniority dimension here. A senior engineer with deep context on a codebase will be confident in changes that a newer team member shouldn't ship without review—and that's fine. Conversely, if a senior engineer is working in an unfamiliar area, they should seek review too. Experience and context determine confidence, not title alone.

There's also a practical reality: PRs that sit waiting for review block other work. Sometimes the cost of waiting days for a review on a low-risk change is higher than the risk of shipping it. Use your judgment, and when in doubt, bias toward unblocking the team while keeping quality high.

The engineer who owns the PR decides the appropriate process based on:

- **The repository and its audience** — an OSS library used by thousands has a different risk profile than an internal tool.
- **The complexity and blast radius** — a core library refactor warrants more scrutiny than a docs fix.
- **Your confidence in the result** — if you're not sure the AI got it right, get another set of eyes on it.
- **The pace of the project** — waiting days for a review on a low-risk change can be worse than shipping it and getting feedback after.

### 3. Draft PRs and Labels

**Draft PRs are encouraged.** Use them freely for experimentation, AI-generated work-in-progress, or anything you're not confident in yet. A messy draft PR is fine—that's what drafts are for. Don't be ashamed of a rough draft; be clear that it *is* a draft. For our OSS repos (which support GitHub's draft PR feature), use draft status to signal work-in-progress. For private repos, use labels to communicate the same intent.

We have existing labels to help signal PR status to the team. Use them:

- **AI on / AI off** — indicates whether AI tooling was used in the PR.
- **WIP (Work in Progress)** — this PR is not ready to merge. Could be an experiment, a conversation starter, or active work-in-progress. Equivalent to draft status on repos that don't support GitHub's draft PR feature.
- **Draft status (OSS repos)** — use GitHub's built-in draft feature on open-source repositories to clearly signal the PR isn't ready for merge.

The goal is clear communication. Your teammates should never have to guess whether a PR is ready to merge, needs review, or is just an experiment. These are the same good engineering practices we've followed long before AI—we're just applying them to a new context. This is an area where we're actively learning as a team, and we're open to feedback on what's working and what isn't.

### 4. Self-Review Is Non-Negotiable

Before merging any AI-assisted code, review it as if someone else wrote it—because something else did. Watch for the kinds of problems AI tends to introduce:

- Subtle performance regressions (e.g., unnecessary network calls, missing caching)
- Skipped or weakened tests that give false confidence
- Breaking changes in adjacent systems the AI didn't account for
- Plausible-looking code that solves the easy part while creating a new hard problem

AI is excellent at solving well-defined problems. It can struggle with the subtle, contextual issues that experienced engineers catch instinctively. That's your value. Apply it. (Worth noting: *Anthropic's own research* found that engineers who actively engage with AI output—asking why, debugging, requesting explanations—retain their skills and judgment. Those who passively delegate don't. How you use AI matters more than whether you use it.)

We also use **automated AI code review tools**—Claude reviews, Greptile, and CodeRabbit—on our repositories. These tools catch issues that humans miss and provide a consistent quality baseline. Treat their comments the same way you'd treat a colleague's review: address what's valid, push back on what's not, and file follow-up issues for anything that's out of scope for the current PR. The same principle applies: small, focused PRs that get merged cleanly and frequently.

### 5. CI Must Pass

No PR should be merged with failing CI. No tests should be skipped to make CI pass. If AI-generated code breaks tests, fix the code—don't skip the tests. Skipped tests are invisible debt that compounds silently.

**Beyond CI:** Today's AI coding agents can do more than just write code and run automated tests. You can push them to perform manual verification—monitoring Chrome, checking browser logs, testing user flows, and capturing screenshots or GIFs as proof that things work as expected. Some of our most important validations are the ones that only happen on a contributor's local machine: testing flows end-to-end, verifying UI behavior, checking edge cases that automated tests don't cover. If you have your agents run tests or verify changes, challenge them to show you proof—screenshots, console output, GIF recordings of the flow working. Trust but verify.

### 6. Match Rigor to Risk

Not every change carries the same risk. Apply the right level of scrutiny to the right kind of work:

- **High-risk** (core libraries, migrations, infrastructure, performance-sensitive code): Peer review by someone with context. Test thoroughly. Consider the blast radius.
- **Medium-risk** (feature work, non-trivial bug fixes): Self-review at minimum. Peer review recommended if you're unsure.
- **Low-risk** (docs, small config tweaks, well-tested straightforward changes): Use your judgment. You're a professional.

### 7. OSS vs. Client Work

Open-source projects and client projects have different risk profiles. Client work has its own deployment and QA processes. OSS has its own nuances: changes merged to the main branch don't always go directly to users—we publish release candidates and test before cutting a final release. But a published release needs to be rock-solid, because thousands of developers depend on it. Be thoughtful about the context you're operating in and calibrate your process accordingly.

### 8. Engineering Standards Apply—Always

Our engineering standards don't change because AI wrote the code. These are the same practices that make us professional engineers, and they apply to every line of code regardless of origin:

- **Never push directly to master.** Always create feature branches and use PRs. Always include issue numbers in PR descriptions with "Fixes #NNN" or "Closes #NNN" to auto-link and auto-close issues.
- **Run tests locally before pushing.** Don't rely on CI as your first pass—it's too slow. When changing source files, run the corresponding test files to catch issues early.
- **Lint before every push.** Run your project's linter (e.g., *bundle exec rubocop*) and fix all violations before pushing commits. If local linting passes but CI fails, investigate the root cause—never make empty commits to retrigger CI.
- **Keep PRs small and focused.** Prefer small, reviewable changes over large sweeping PRs. Never refactor or "improve" code that isn't directly related to the task at hand. If you see something that should be done separately, stash changes, create a new branch, and open a separate PR.
- **Use meaningful branch names.** Include the issue number and 2–3 keywords from the issue title (e.g., *jg/1234-ssr-hydration-fix*). Generic names like *fix-1234* are useless when scanning dozens of branches.
- **Understand before accepting.** When CI fails, your first move can be to have an AI agent diagnose and fix it—that's fine and often efficient. But review the fix. If the AI is flailing after repeated attempts, escalate: try a different model (e.g., switch from Opus to Codex), provide more context, or look at the error yourself. The key is knowing when CI was passing and when it broke, and giving your agents targeted guidance rather than letting them guess blindly. Always review the changed files and the automated code review comments—they often surface insights the AI missed.
- **Verify what was actually tested.** This is primarily an instruction for your AI agents: they should never claim tests pass without actually running them. Modern agents are getting better at this, but it's still worth challenging them—ask what was tested, what wasn't, and whether the testing covers the actual change. As the executive chef, you should know what verification was done before you ship.

These standards are codified in each project's **CLAUDE.md** file, which provides project-specific instructions to Claude Code and serves as a living reference for engineering expectations. If your project doesn't have one yet, consider creating one—it helps both human and AI contributors follow the same standards.

## Culture and How We Work Together

### Focus on What, Not How

Leadership defines *what* needs to be done. *How* you do it is your decision. You are senior engineers—we hired you for your judgment. Nobody will tell you which tools to use, how many AI sessions to run, or second-guess your workflow. If a task takes longer than expected, that's information about the problem's complexity, not a signal to work differently.

### Recognize the Hard Work

When we share AI success stories, it's to inspire everyone to explore these tools—not to diminish the humans doing critical work. The engineers who debug, stabilize, and ship production-quality code deserve recognition, especially when they're the ones making AI output actually shippable. Let's celebrate both the tooling wins and the people who make them real.

### Share What You Learn

We all benefit when people share their experiences with AI tools—what worked, what didn't, where it saved hours, where it created headaches. Use our Slack channels for this:

- **#ai-programming-tools** — tips, techniques, articles, and discussions about AI-assisted development.
- **#ai-programming-wins** — share your successes. When AI saves you hours or surprises you, post it here so we can all learn.
- **#ai-fuckup-postmortem** — equally important, but reserve this for *non-trivial, instructive failures*—not every small mistake. AI will make little errors constantly; if you're not seeing them, you're probably not pushing hard enough. Sometimes the fix is just switching to plan mode or rewording a prompt. Post here when there's a real lesson: a pattern others should watch for, a failure mode worth understanding, or a workaround worth sharing. Frame it constructively—the goal is learning, not "AI sucks."
- **#ai-vibe-coding** — for experimental, exploratory AI use. Vibe coding is great for learning—just know when to shift from vibe to rigor.

The more transparent we are about real results—both the wins and the fuckups—the better our collective judgment becomes.

### When Things Go Wrong

If a PR—AI-assisted or not—causes problems for other team members, that's something we address together as a team. It's not about blame; it's about learning and adjusting the process for that kind of change. We all make mistakes. The goal is to catch them early and learn from them.

## Staying Current

AI tools are evolving fast. What's true about their capabilities and limitations today may not be true in six months. This policy will evolve with them. We'll adapt together based on evidence and real-world results—not hype, and not fear.

Every engineer is encouraged to:

- Explore new AI tools and features as they become available
- Develop your own judgment about when AI helps and when it doesn't
- Share discoveries and lessons with the team
- Push back if something in this policy isn't working—this is a living document

### Shared Team Tooling

We maintain an open-source repository at **github.com/shakacode/claude-code-commands-skills-agents** — our team's collective knowledge base for AI-assisted development workflows. It includes custom slash commands, agents, templates, documentation guides, and GitHub Actions. Because it's open source, our clients and the broader community benefit too.

**Commands:**

- **/review-all-prs** — comprehensive code review on single or multiple PRs covering code quality, security, performance, and testing.
- **/self-review** — detailed analysis of your uncommitted changes before you open a PR. Catches issues before they reach review.
- **/security-review** — scans code against the OWASP Top 10 checklist. Especially useful for AI-generated code that may introduce vulnerabilities the AI doesn't flag.
- **/optimize** — identifies performance bottlenecks with categorized improvement suggestions.
- **/merge-commit-msg** — generates structured merge commit messages from PR changes.

**Agents and Automation:**

- **pr-testing-agent** — analyzes the scope of a PR and runs only the relevant test suites, saving CI time and giving faster feedback.
- **GitHub Actions** — automated PR review workflows and mention-based interaction handlers that run AI review on every PR automatically.

**Templates and Guides:**

- **CLAUDE.md and AGENTS.md templates** — reference configurations for project-specific engineering standards. CLAUDE.md provides instructions to Claude Code; AGENTS.md enables cross-tool compatibility with Cursor, Codex, and others.
- **Documentation guides** — five guides covering Claude integration, custom agent creation, automation hooks, Codex CLI workflows, and practical strategies.
- If you've built a useful command, agent, skill, or workflow—contribute it back. The repo is a team resource, and your contributions help everyone level up.

## Summary

1. **Own your work.** You're the executive chef. Whatever tools you use, the output is yours.
2. **Review case by case.** Pre-review, post-review, or self-review—you decide based on risk and context. Use drafts and labels to communicate clearly.
3. **CI must be green.** Never skip tests to ship faster.
4. **Match rigor to risk.** High-impact changes get more scrutiny. Low-risk changes are your call.
5. **Stay current.** Explore AI tools. Share what you learn. This is part of being a great engineer.
6. **Celebrate the people.** Tools are tools. Engineers make them work.
7. **Keep talking.** This policy evolves with our experience. Your feedback shapes it.

---

*The bottom line:* The only thing different about AI tools is their power and pace of change. The fundamentals of our craft—ownership, quality, judgment, continuous learning—haven't changed. Each of us is the executive chef of our kitchen. Let's keep raising the bar together.

---

*This is a draft.* Please add comments, suggest edits, and share your perspective. The best version of this policy is one we've built together.

— Justin
