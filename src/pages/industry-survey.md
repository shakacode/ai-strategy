---
layout: ../layouts/Article.astro
title: "How 10 Companies Are Governing AI-Assisted Development in 2026"
description: "A survey of AI development policies across Shopify, Meta, GitLab, Anthropic, and more — with lessons for engineering leaders"
author: "Justin Gordon"
date: "February 2026"
---

## Executive Summary

AI-assisted development has moved from experimental to expected across the tech industry. This document reviews how 10 major companies and one landmark research program are approaching AI in their engineering organizations. The goal: identify what ShakaCode can learn from, adopt, or intentionally diverge from.

The spectrum ranges from **Shopify and Meta** (AI usage is mandatory and tied to performance reviews) to **Amazon and GitLab** (provide tools and governance frameworks, let teams decide). **Google's DORA research** provides the most rigorous empirical evidence: AI amplifies what's already there—strong teams get stronger, dysfunctional teams get worse.

**Key takeaway:** No serious company is ignoring AI-assisted development. The differentiator is how thoughtfully they govern it. The best-performing organizations pair aggressive AI adoption with strong testing, human review, small batch sizes, and clear ownership—exactly the direction ShakaCode's policy is heading.

## Company-by-Company Review

### Shopify

**Stance:** AI usage is a mandatory baseline expectation for all employees.

In March 2025, CEO Tobi Lütke issued a company-wide memo declaring that "using AI effectively is now a fundamental expectation of everyone at Shopify." This was not aspirational—it came with teeth. Before teams can request additional headcount, they must demonstrate why AI cannot do the work. AI proficiency has been incorporated into Shopify's 360-degree review cycle, with peers and managers evaluating how "AI native" each person is. Engineers have access to pre-configured tools (GitHub Copilot, Cursor, Claude Code, chat.shopify.io) and are expected to use them reflexively—as naturally as a keyboard.

**What's notable:**

- Prototyping is expected to be "dominated" by AI exploration.
- Learning is self-directed but collaborative—share what works.
- Engineers are still expected to maintain the ability to review and identify issues in AI-generated code.
- Pragmatic Engineer's Farhan Thawar coverage showed Shopify aims for 90–95% AI usage while retaining manual review skills.

*ShakaCode relevance:* ShakaCode's policy is directionally similar—AI is a professional responsibility—but less prescriptive. We don't tie AI usage to performance reviews or headcount gating. Our "executive chef" model gives engineers more autonomy in how they use AI, which is appropriate for our team size and culture.

### Meta

**Stance:** AI usage is formally tied to performance reviews for all employees starting 2026.

Meta has taken the most aggressive documented stance. Mark Zuckerberg stated the company will begin automating midlevel software engineering roles while hiring more AI-focused engineers. Starting in 2026, all employees are formally evaluated on "AI-driven impact" in their performance reviews. Meta invested $66–72 billion in AI compute infrastructure for 2025 alone—an increase of $30B year-over-year—and created a dedicated Superintelligence Labs division.

*ShakaCode relevance:* Meta's approach is more heavy-handed than we need. Tying performance reviews to AI metrics risks incentivizing quantity over quality—the exact problem our petition highlighted. However, Meta's signal is clear: the industry is moving toward AI proficiency as a core engineering competency, not an optional skill.

### Coinbase

**Stance:** Fired engineers who did not adopt AI tools. Targeting 50% AI-written code.

Coinbase CEO Brian Armstrong took the most aggressive action of any public company: engineers who refused to use AI tools (specifically Cursor and Copilot) were let go. The company set an explicit target of 50% AI-written code. This is the extreme end of the spectrum and generated significant controversy.

*ShakaCode relevance:* This is a cautionary example. Forcing adoption through fear creates compliance, not competence. Our approach of building a supportive culture (Slack channels, shared tooling, learning from failures) is more sustainable. That said, Coinbase's direction confirms the industry trend: AI tool proficiency is becoming table stakes.

### Anthropic

**Stance:** Encourages aggressive AI usage with transparent acknowledgment of trade-offs.

Anthropic—the company behind Claude—encourages its people to use AI "as aggressively as possible" to push capability boundaries. Claude Code was used extensively internally before its public launch. Most technical employees use it daily. The company published candid research acknowledging that AI has the least productivity gains for design and planning tasks, and expressed concern about engineers potentially losing deeper technical competence if they over-rely on AI. Their research on skill formation found that engineers who actively engage with AI output (questioning, debugging, understanding) retain their skills, while those who passively delegate don't.

*ShakaCode relevance:* Anthropic's transparency about the trade-offs is refreshing and aligns with our approach. Their skill formation research directly informed our policy's emphasis on active engagement over passive delegation. The "aggressive but thoughtful" stance mirrors what we're doing.

### Google (DORA Research Program)

**Stance:** Rigorous empirical research showing AI amplifies existing team dynamics—good and bad.

Google's DORA (DevOps Research and Assessment) program provides the industry's most rigorous data on AI's impact on software delivery. The 2025 report found that 90% of developers now use AI at work, up significantly from prior years. AI adoption is now linked to higher software delivery throughput—but only when paired with the right practices.

**Critical finding:** "AI doesn't fix a team; it amplifies what's already there." Strong, well-organized teams use AI to become more productive. Teams with existing problems find that AI magnifies their dysfunctions.

**The DORA AI Capabilities Model** identifies seven capabilities that magnify positive AI impact:

1. Clear AI policies
2. Healthy data ecosystems
3. User-centric focus
4. Strong version control practices
5. Working in small batches
6. Quality internal platforms
7. Organizational learning culture

DORA also found that without robust control systems, increased AI-driven development leads to instability. Protective mechanisms include: **strong automated testing, mature version control, fast feedback loops, and working in small batches**. Notably, 30% of respondents still have little or no trust in AI-generated code, highlighting the importance of human review.

*ShakaCode relevance:* DORA's findings validate almost every aspect of our policy: clear ownership, strong testing, small focused PRs, case-by-case review, and a learning culture. Their "amplification" finding is particularly relevant—our policy's emphasis on the executive chef model and engineering standards is exactly the kind of strong foundation that makes AI adoption productive rather than destructive.

### Amazon/AWS

**Stance:** Provides tools and governance frameworks; lets teams decide adoption level.

Amazon launched Amazon Q Developer as its primary AI coding assistant and announced three "frontier agents" at re:Invent 2025, including Kiro—an autonomous coding agent that can operate for hours or days but requires developer approval before merging changes. Amazon's approach emphasizes governance: their AgentCore platform lets developers set boundaries for AI agents with three network access levels, sandboxing, and comprehensive logging. The philosophy is "tool and framework first, mandate never."

*ShakaCode relevance:* Amazon's governance model—specifically the requirement that agents need human approval before merging—aligns with our "human always accountable for the merge decision" principle. Their layered access control approach is worth considering as AI agents become more autonomous in our workflows.

### GitLab (Deep Dive)

**Stance:** Evolving guidelines rather than rigid rules, backed by the most comprehensive governance and transparency infrastructure in the industry.

GitLab stands out as the company with the most detailed, publicly documented AI development practices. Their entire handbook is open, their AI Transparency Center is public, and they achieved ISO/IEC 42001 certification (the international standard for AI Management Systems) in September 2025. This section goes deeper because GitLab's approach offers the most directly applicable lessons for ShakaCode.

#### The Five-Phase AI Development Playbook

GitLab published a formal five-phase process for developing AI features, documented at docs.gitlab.com:

1. **Prepare:** Teams decide if approved models satisfy their requirements or propose new models for approval. They design testing and evaluation strategies and identify required datasets. This happens during planning, before any code is written.

2. **Develop:** Build the feature with iterative prompt engineering. Integrate through their centralized AI Gateway rather than calling models directly.

3. **Test and Evaluate:** Validate quality, performance, and security. All third-party AI provider calls are mocked in tests with deterministic assertions. They run a Central Evaluation Framework (CEF) scoring accuracy, precision, recall, token usage, conciseness, and coherence.

4. **Launch:** Controlled rollouts using feature flags. Start with internal teams, then gradual expansion with comprehensive monitoring.

5. **Improve:** Iteratively refine based on real-world usage data and user feedback. Adjust prompts, model selection, or architecture as needed.

#### Governance and Data Protection

GitLab's governance model is the most granular of any company surveyed. Admins have namespace-level control over which AI models power different features. Teams in regulated industries can restrict their environment to approved models only. Key data commitments: no customer inputs or outputs are used to train GitLab models, vendors are contractually prohibited from using data for their own purposes, and code is scanned with Gitleaks to detect and remove secrets before any data is transmitted to AI providers.

**File and path exclusion:** Premium and Ultimate customers can exclude specific files and directory paths from AI access using project-level settings and path-based rules. This means sensitive configuration files, credentials, and proprietary business logic can be shielded from AI context windows entirely, with audit visibility for compliance tracking.

**Agent governance:** GitLab treats AI agents as privileged identities, linked to human operators through "composite identities" for accountability. They maintain "paved roads"—pre-approved models and secure integration patterns—to prevent AI assistants from suggesting insecure code or exposing secrets. Their Duo Agent Platform (generally available in GitLab 18.8) includes an AI Catalog where teams can create, publish, and share approved agents organization-wide.

#### AI Code Review Standards

GitLab's approach to AI-generated code review is layered. AI performs initial merge request reviews, generates PR summaries, and suggests improvements directly in the UI. But critically, AI-generated fixes use JSON schema validation and guardrails to ensure predictable, actionable outputs. Traditional rule-based security scanners remain the source of truth for detection; AI adds context awareness, prioritization, and concrete fix proposals on top. Their agentic SAST vulnerability resolution (powered by Claude 3.5 Sonnet) can analyze vulnerabilities, generate fixes, and validate them through automated testing—but with confidence scoring so humans know how much to trust each suggestion.

#### Addressing the "AI Paradox"

GitLab's CTO Sabrina Farmer (ex-VP Engineering at Google) frames a critical insight: code generation represents only about 20% of developer time. The other 80% goes to meetings, writing tests, documentation, and coordination. GitLab's AI strategy focuses on automating that 80%—not just making the 20% faster. Their Duo Agent Platform includes specialized agents for planning, security analysis, test generation, documentation, and research. This "AI paradox" framing aligns with what we see at ShakaCode: the biggest productivity wins often come from AI helping with the surrounding work, not just the code itself.

#### Leadership Vision

GitLab's current CEO Bill Staples puts the business case bluntly: survey data suggests $28,249 in annual savings per developer from AI investments, with $750+ billion in global value at stake. Former CEO Sid Sijbrandij's perspective is more technical: AI models will gradually consume more of what is currently procedural code, but trying to optimize code generation alone will break everything downstream (QA, security, operations). The implication: AI must be embedded across the entire software delivery lifecycle, not just the coding step.

#### Measuring AI Impact

GitLab provides an AI Impact Analytics Dashboard tracking: license and adoption analytics (seats assigned vs. used), code suggestion acceptance rates, chat interactions, and per-user engagement metrics. They calculate a "Monthly Code Suggestions Usage Rate" as a ratio of unique AI users to total contributors. This level of measurement helps teams understand actual adoption patterns rather than just mandating usage.

**ShakaCode relevance:**

- **File exclusion for client work:** We should implement path-based exclusion rules in our CLAUDE.md files for client projects with sensitive data. This is straightforward and high-value.

- **The "AI paradox" insight:** If only 20% of developer time is coding, our AI strategy should explicitly address the other 80%. We're already doing this with AI code reviews, but could do more with test generation, documentation, and planning agents.

- **Confidence scoring:** GitLab's approach of attaching confidence scores to AI suggestions helps engineers calibrate trust. We could adopt a similar mindset: treat AI output skepticism as proportional to the complexity and risk of the change.

- **Agent governance:** As we run more long-running AI agent sessions, GitLab's "composite identity" model (linking agent actions to human operators) is worth considering. Every agent action should trace back to the engineer who launched it.

- **Evolving guidelines > rigid rules:** GitLab's iterative approach—publish, gather feedback, refine—is exactly what we're doing with our policy as a Google Doc open for team comment. This is the right pattern for a fast-moving domain.

### Microsoft/GitHub

**Stance:** Massive structural investment; positioning GitHub as central AI development hub.

Microsoft restructured in January 2025, creating a "Core AI Platform and Tools" division merging GitHub, developer tools, and AI platform teams. GitHub's January 2026 VS Code update transformed the editor into a multi-agent orchestration hub. Their strategic vision positions GitHub as the central command center for AI-driven development workflows—not just code storage. While they haven't published explicit mandatory usage policies, the organizational restructuring signals that AI-native development is the expected default.

*ShakaCode relevance:* Microsoft's infrastructure investment confirms that AI-first development tools will be the default IDE experience within 1–2 years. Our team's early adoption of multi-agent workflows positions us ahead of this curve.

### Atlassian

**Stance:** Framework-based approach with compliance focus and responsible AI principles.

Atlassian developed their HULA (Human-in-the-Loop Automation) framework for AI-assisted coding, created Atlassian Intelligence as their virtual agent platform, and published Responsible Technology Principles. They joined the EU AI Pact in September 2024, signaling their compliance-forward approach. Their engineering organization uses a federated model: a central AI team builds shared infrastructure, while product teams handle AI-driven development decisions.

*ShakaCode relevance:* Atlassian's HULA framework name itself is instructive: "Human-in-the-Loop." This echoes our executive chef model. Their federated approach (shared AI infrastructure, team-level decisions) maps to how we use shared tools like claude-code-commands-skills-agents while letting engineers choose their own workflows.

## Comparison Matrix

How each company's approach compares across key policy dimensions:

| Company | AI Mandatory? | In Perf Reviews? | Review Policy | Governance | Approach |
|---------|---------------|------------------|---------------|-----------|----------|
| Shopify | Yes | Yes | Review expected | Headcount gating | Mandate |
| Meta | Yes | Yes (2026) | Not specified | Perf metrics | Mandate |
| Coinbase | Yes (fired) | Implied | Not specified | Usage targets | Coercive |
| Anthropic | Encouraged | No | Active engagement | Research-informed | Cultural |
| Google/DORA | N/A (research) | N/A | Strong review + testing | 7 capabilities | Evidence-based |
| Amazon | Optional | No | Approval before merge | Sandboxing + logging | Framework |
| GitLab | Optional | No | Manual review + security | Model selection, context control | Evolving guidelines |
| Microsoft | Structural | Not documented | Not specified | Platform investment | Infrastructure |
| Atlassian | Optional | No | Human-in-the-loop | HULA framework, EU AI Pact | Principles |
| ShakaCode | Expected | No | Case-by-case ownership | Exec chef + CLAUDE.md | Balanced |

## Key Patterns Across the Industry

### 1. AI Proficiency Is Becoming Table Stakes

Every company surveyed either mandates AI usage (Shopify, Meta, Coinbase), strongly encourages it (Anthropic, ShakaCode), or is investing billions to make it the default workflow (Microsoft, Amazon). No serious tech company is treating AI tools as optional for engineers. The question is not *whether* to adopt AI—it's *how to adopt it well*.

### 2. The Governance Spectrum

Companies fall on a spectrum from coercive (Coinbase: fired engineers) to cultural (Anthropic: encouraged aggressive use with transparent trade-off acknowledgment). The mandate-heavy approaches (Shopify, Meta) generate faster adoption metrics but risk resentment and quality shortcuts. The framework approaches (Amazon, GitLab, Atlassian) preserve autonomy but may leave adoption patchy. ShakaCode's position—"expected but with engineering autonomy"—is a thoughtful middle ground.

### 3. Human Review Remains Non-Negotiable

Every company that addresses code quality—Amazon, GitLab, Atlassian, DORA—requires human review of AI-generated code before it ships to production. Even Shopify, which pushes 90–95% AI usage, explicitly requires engineers to maintain the ability to review and identify issues. Amazon's Kiro agent requires human approval before merging. Atlassian named their entire framework "Human-in-the-Loop." The consensus is clear: AI writes code, humans decide whether it ships.

### 4. DORA's Amplification Effect Is the Key Insight

The most important finding from any source is DORA's: "AI doesn't fix a team; it amplifies what's already there." Teams with strong engineering practices (good testing, version control, small batches, fast feedback) see AI make them more productive. Teams with weak foundations see AI amplify their problems. This means investing in engineering discipline is not competing with AI adoption—it's the prerequisite for making AI adoption work.

### 5. The Skills Formation Concern Is Real

Anthropic's own research found that passive AI delegation degrades engineering skills, while active engagement (questioning, debugging, understanding) preserves and sharpens them. DORA's trust data shows 30% of developers still don't trust AI output. The industry is converging on a view that AI is a power tool that requires skill to use well—not a replacement for skill. This is exactly the executive chef framing: the tool is powerful, but the chef's judgment is what makes it produce great results.

## Ideas Worth Considering for ShakaCode

Based on this review, here are specific elements from other companies that could strengthen or complement our existing policy:

1. **Context exclusion for sensitive client files (from GitLab).** GitLab lets teams block specific files and directories from being used as AI context. For client projects with sensitive data, this is a practical security measure we should consider implementing in our CLAUDE.md configurations.

2. **Agent approval gates (from Amazon).** As AI agents become more autonomous (running for hours unsupervised), Amazon's pattern of requiring human approval before merging becomes increasingly relevant. Our policy already requires this implicitly through engineer ownership, but making it explicit for long-running agent sessions may be worth adding.

3. **Structured learning from failures (from DORA).** DORA's "organizational learning culture" capability maps directly to our #ai-fuckup-postmortem channel. We could formalize this slightly: periodic retrospectives (monthly?) that synthesize learnings from the channel into actionable team guidelines.

4. **AI onboarding playbook (inspired by GitLab).** GitLab's five-phase AI feature development playbook is a structured approach to AI work. We could create a lighter version: a "Getting Started with AI at ShakaCode" guide in the boosters repo that helps new team members get productive quickly with our tools and workflows.

5. **Transparent trade-off acknowledgment (from Anthropic).** Anthropic's candor about where AI falls short (design/planning tasks, potential skill degradation with passive usage) builds trust. Our policy could benefit from explicitly naming where AI is weakest in our experience, not just its strengths.

6. **Small batch emphasis (from DORA).** DORA specifically calls out that AI can lead to larger changesets, which are inherently riskier. Our "keep PRs small and focused" standard addresses this, but we could be more explicit: AI makes it easy to generate large changes. Resist the temptation. Small PRs are even more important with AI, not less.

## Where ShakaCode Stands

Compared to the industry, ShakaCode's AI Tools Policy is well-positioned. We're more progressive than companies that treat AI as optional, more humane than those that tie it to performance reviews or termination, and more practical than those that only provide abstract principles. Our executive chef model gives engineers ownership and autonomy while maintaining accountability—a balance that none of the companies surveyed have articulated as clearly.

The DORA research provides the strongest validation of our direction: clear policies, strong engineering practices, small batches, human oversight, and a learning culture are exactly the capabilities that make AI adoption productive. We have all of these in some form. The policy formalizes them.

The industry consensus is unmistakable: AI-assisted development is the present, not the future. The companies that thrive will be those that adopt it aggressively *and* govern it thoughtfully. That's exactly what we're building.

---

**Sources:** Shopify CEO memo (March 2025), Pragmatic Engineer coverage of Shopify, TechCrunch/CNBC/BetaKit reporting, Meta performance review announcements (WinBuzzer, Feb 2026), Coinbase CEO AI mandate (Final Round AI), Anthropic "How AI Is Transforming Work" research, DORA 2024/2025 State of DevOps and AI reports (Google Cloud), Amazon re:Invent 2025 announcements, GitLab AI Feature Development Playbook and Handbook, Microsoft/GitHub VS Code and organizational restructuring coverage, Atlassian HULA framework and EU AI Pact documentation.
