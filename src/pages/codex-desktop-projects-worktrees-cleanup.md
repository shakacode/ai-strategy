---
layout: ../layouts/Article.astro
title: "Codex Desktop App: Projects, Worktrees, Threads, Subagents, and Cleanup"
description: "A practical guide to Codex desktop app workspace behavior: what Worktree mode means, when to create a new project, how subagents and custom agents work, and how auto-cleanup and retention settings work."
author: "ShakaCode"
date: "March 2026"
---

If Codex desktop app terminology feels fuzzy, this mental model is the one that stays consistent as of March 26, 2026:

- A **project** is an entry in your sidebar tied to a local folder/workspace.
- A **thread** is a conversation inside that project.
- A **Codex-managed worktree** is a separate checkout Codex can use for thread work.
- A **permanent worktree** is a long-lived separate checkout that appears as its own project and is not auto-deleted.
- A **subagent** is a child agent Codex can spawn inside a task when you explicitly ask it to parallelize part of the work.

## What Worktree Mode Means in the App

In Codex app terms, Worktree mode means your thread runs in a different checkout than your main Local checkout for that repo.

That separation prevents common collisions:

- New files generated in one checkout do not appear in the other by accident.
- Dependency installs and build artifacts stay scoped to the checkout you are using.
- Branch and working-copy state in one checkout does not disrupt your active Local checkout.

This is why permanent worktrees are useful for longer efforts: they give you a stable, separate workspace without constant context switching.

## Where Subagents Fit

Subagents are the new piece that trips people up. They are not another project in the sidebar. They are not a permanent worktree. They are not the same thing as opening a fresh top-level thread.

Think of a subagent as a focused helper inside your current task. Codex can spawn several of them in parallel, wait for all of them, and then give you one combined answer.

Use this rule of thumb:

- **For project decisions**, use the guidance in "When to Create a New Project vs Reuse One" below.
- **Create a new thread** when you want a separate top-level conversation in the same project.
- **Ask for subagents** when you want parallel work inside the current task.

OpenAI's current docs say subagent activity is surfaced in the Codex app and CLI. Current Codex releases enable subagent workflows by default. Codex only spawns them when you explicitly ask, and subagent workflows consume more tokens than comparable single-agent runs.

## When Subagents Make Sense

Subagents are a good fit when the work naturally fans out:

- Reviewing one PR from multiple angles, like security, bugs, test flakiness, and maintainability.
- Exploring multiple code paths or subsystems in parallel before deciding on a fix.
- Splitting a larger workflow into focused roles, such as exploration, implementation, and docs verification.

Current Codex docs also describe built-in agent roles like `default`, `worker`, and `explorer`, plus custom agents you can define in `config.toml` and `.codex/agents/`. The important mental model in the desktop app is simpler: subagents are about delegation, not about creating another checkout you need to manage manually.

Here are the kinds of prompts where I would actually use them:

- **PR review from multiple angles**: "Review this branch against `main`. Spawn one subagent for security, one for bugs, one for test gaps, and one for maintainability. Wait for all of them and summarize the findings."
- **Codebase exploration**: "I need to understand checkout failures. Spawn one subagent to trace the frontend checkout flow, one to trace the Rails API path, and one to trace Stripe webhook handling. Then give me one merged map."
- **Parallel prep before implementation**: "Spawn one subagent to find existing patterns for this feature, one to identify the tests we will need, and one to verify the framework docs. Then recommend the implementation plan."

The flip side is important too: I would not reach for subagents when the task is a tightly coupled refactor where every step changes the context for the next step. That is usually better handled by one agent working through the problem end to end.

## How to Make Custom Subagents

If by "make subagents" you mean "define my own reusable agent roles," the current Codex docs say the setup lives in Codex config rather than in a special app wizard.

Codex already ships with built-in agents like:

- `default`
- `worker`
- `explorer`

To make your own custom agent, create a TOML file in one of these locations:

- `.codex/agents/` for project-specific agents
- `~/.codex/agents/` for personal agents you want across projects

Each custom agent file needs these fields:

- `name`
- `description`
- `developer_instructions`

Then you can optionally add things like:

- `model`
- `model_reasoning_effort`
- `sandbox_mode`
- `nickname_candidates`
- `mcp_servers`

For example:

```toml
name = "reviewer"
description = "PR reviewer focused on correctness, regressions, and missing tests."
developer_instructions = """
Review code like an owner.
Lead with concrete findings.
Prioritize bugs, regressions, security issues, and missing tests.
"""
sandbox_mode = "read-only"
```

Global subagent settings still live in your `config.toml` under `[agents]`, where current docs describe controls like:

- `agents.max_threads`
- `agents.max_depth`

So the practical setup is:

1. Create a custom agent file.
2. Keep the instructions narrow and opinionated.
3. Ask Codex to spawn that agent by name inside a task.

That is why I think of "making subagents" as mostly a configuration problem, not a project/worktree problem.

## The "I Want 5 Things Happening At Once" Case

This scenario is where the distinctions matter most.

If you want **5 separate things happening at the same time on one repo**, the default answer is:

- **5 top-level threads**
- usually **5 Codex-managed worktrees**
- usually **0 permanent worktrees**

That is the cleanest setup when the five efforts are actually independent. One thread per task keeps each checkout isolated.

If you want **1 task to fan out 5 ways**, the answer is different:

- **1 top-level thread**
- **5 subagents**

That is the right pattern when the work belongs to one parent task and you want one merged result back.

If you want **1 long-running lane with many conversations over time**, that is when a permanent worktree enters the picture:

- maybe **1 permanent worktree**
- multiple threads over days or weeks

I would not choose one permanent worktree just because I want five things running at once. I would choose one permanent worktree only if all of those threads belong to the same durable stream of work and I want that checkout to stay around.

## When to Create a New Project vs Reuse One

Use this rule of thumb:

- **Create a new project** when you are switching to a different folder/repository, or when you want a separate long-lived permanent worktree from the same repo.
- **Reuse an existing project** when you are still in the same folder and just starting another task; create a new thread instead.

If your work will continue over many sessions in the same repo and you want hard isolation, create a permanent worktree project.

Subagents do not change that decision. They live inside the task you are already running.

## How to Create a Permanent Worktree Project

In the sidebar:

1. Find the project.
2. Open the three-dot (`...`) menu.
3. Choose the permanent worktree option.

Codex creates a new project backed by a permanent worktree. You can run multiple threads from that project, and Codex does not auto-delete it.

## Why Codex Makes You Think About Worktrees

This part feels fussy until you realize Codex is exposing a real Git constraint instead of inventing random product vocabulary.

Codex can either work in your current checkout or in a separate checkout. That choice matters because commands, generated files, dependency installs, build outputs, and branch state all happen in a real directory somewhere. If Codex hid that distinction, two threads could quietly step on each other in ways that are hard to debug.

So the app makes you choose between:

- **Local**: work in the checkout you already have open.
- **Worktree**: give Codex an isolated checkout so it can work without colliding with your Local setup.

That is why this shows up in the UI at all. Codex is managing real checkouts, not just imaginary chat threads.

## Permanent Worktree vs Just Making Another Folder

This is the part that deserves a more direct explanation.

A permanent worktree is, yes, another folder on disk. But it is not just some random copied folder. Per the current Codex docs, Git worktrees give you another full checkout of the repo while sharing the same Git metadata about commits and branches.

That means a permanent worktree project is basically:

- another long-lived checkout of the same repo
- understood by Codex as a first-class project in the sidebar
- safe from auto-cleanup
- able to host multiple threads over time

If you just make another folder, there are really two possibilities:

- **You copy the folder manually**. That is just a duplicate directory. Codex does not understand it as related Git worktree state, and you now have a heavier, easier-to-drift copy.
- **You clone the repo again**. That can work, but it is heavier than a worktree because you now have another full `.git` directory, another fetch/pull lifecycle, and another place for branch state to drift.

So why use a permanent worktree project instead of one of those?

- It stays integrated with the same repo identity.
- It fits the Codex handoff and sidebar model cleanly.
- It is meant for long-running work, not single-thread disposable work.

My summary would be: a permanent worktree project is Codex's "make me another serious checkout of this repo" button.

## When You Want Zero vs One Permanent Worktree

This is the simplest version of the decision.

You want **zero** permanent worktrees when:

- your Local checkout is already your main home base
- most Codex tasks are short-lived and disposable
- you do not expect to come back to the same isolated checkout across many sessions
- handing work back to Local is enough

In other words, zero permanent worktrees is the default when you mostly want Codex-managed worktrees to be temporary scratch space.

You want **one** permanent worktree when:

- you have one long-running stream of work you want to keep isolated from Local
- you expect to come back to that same checkout repeatedly over days or weeks
- you want multiple threads to share that same long-lived environment
- you do not want Codex to auto-clean it up

In other words, one permanent worktree makes sense when you want a second real home base for the same repo.

If you are unsure, choose **zero** first. You can always promote your workflow later when a long-running lane actually appears.

## Why You Might Want More Than One Permanent Worktree

Most people probably do not.

If you are asking this question, the right default is usually:

- one normal Local checkout
- temporary Codex-managed worktrees for one-off tasks
- zero or one permanent worktree for a long-running effort

Multiple permanent worktrees only start to make sense when you have multiple long-running lanes that should stay isolated for weeks, not hours. For example:

- **Day-to-day work vs. a big upgrade**: one permanent worktree for normal product work, another for a multi-week Rails or React upgrade.
- **Trunk vs. release support**: one permanent worktree tracking current development, another holding a release or hotfix branch you need to revisit regularly.
- **Different client or deployment tracks**: one permanent worktree per long-lived branch when the work really is separate enough that you keep bouncing between them.

The key idea is not "one repo needs many permanent worktrees." The key idea is "some repos have more than one long-lived stream of work."

If that is not you, do not create multiple permanent worktrees just because the feature exists.

## Auto-Cleanup: When It Happens

Codex cleanup is lifecycle-based, not a fixed nightly schedule.

By default, Codex keeps your most recent **15** Codex-managed worktrees and can remove older ones to stay under that limit.

Codex-managed worktrees are eligible for automatic deletion when:

- The associated thread is archived, or
- Codex needs to evict older worktrees to respect the retention limit.

Codex tries to preserve important worktrees and avoids auto-deleting a managed worktree if:

- The conversation is pinned,
- The thread is still in progress, or
- The worktree is permanent.

Before a managed worktree is deleted, Codex stores a snapshot so restore is possible when reopening.

Subagents do not change this cleanup model. Cleanup is still about Codex-managed worktrees and long-lived checkouts, not about child agents you asked Codex to spawn inside a task.

## How to Configure Cleanup

In Codex desktop app:

1. Open **Settings** (`Cmd+,`).
2. Find worktree cleanup/retention controls.
3. Change the managed-worktree retention limit, or disable automatic deletion if you prefer manual cleanup.

If you never want a checkout auto-deleted, use a permanent worktree.

## Practical Workflow

For most teams, the cleanest workflow is:

1. Keep one project per repo or per permanent worktree you want to preserve.
2. Start a new thread for each top-level task.
3. Ask Codex to spawn subagents only when the work genuinely parallelizes.
4. Default to zero permanent worktrees until you have one clear multi-session lane that deserves its own long-lived checkout.
5. Archive stale threads and remove no-longer-needed projects from the sidebar.
6. If you are unsure whether you need a second permanent worktree, you probably do not.

That keeps your sidebar, disk usage, and mental model under control.

## Sources

- [Codex app: Worktrees](https://developers.openai.com/codex/app/worktrees)
- [Codex app: Features](https://developers.openai.com/codex/app/features)
- [Codex app: Settings](https://developers.openai.com/codex/app/settings)
- [Codex: Subagents](https://developers.openai.com/codex/subagents)
- [Codex CLI: Subagents](https://developers.openai.com/codex/cli/features#subagents)
- [Git Worktree docs](https://git-scm.com/docs/git-worktree)
