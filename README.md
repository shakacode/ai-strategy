# ShakaCode AI Strategy

Published at [ai.shakacode.com](https://ai.shakacode.com)

How ShakaCode approaches AI-assisted development: our governance model, industry research, and open-source tooling.

## What's Here

- **[The Executive Chef Model](https://ai.shakacode.com/executive-chef-model)** — Our framework for AI-assisted development. Every engineer is an executive chef: use whatever AI tools you want, you own what you ship.
- **[AI Tools Policy](https://ai.shakacode.com/ai-tools-policy)** — The internal policy we share with our team. Code review expectations, PR guidelines, quality standards, and how we learn from failures.
- **[Industry Survey](https://ai.shakacode.com/industry-survey)** — How Shopify, Meta, GitLab, Anthropic, Google/DORA, Amazon, and others are governing AI-assisted development.
- **[Response to Team Concerns](https://ai.shakacode.com/response-to-team)** — When our team raised concerns, we responded openly. This is what transparent governance looks like.

## Related

Our AI development toolkit is a separate repo: [shakacode/claude-code-commands-skills-agents](https://github.com/shakacode/claude-code-commands-skills-agents). It includes the slash commands, agents, templates, and GitHub Actions that implement the philosophy described here.

## Contributing

This is an open-source repo. If you disagree with something, think we're missing something, or want to share how your team handles AI governance — open a PR or start a discussion.

We're especially interested in:
- How other teams are implementing governance frameworks
- Research we should be citing
- Practical tooling and workflow improvements
- Corrections or clarifications

## Development

This site is built with [Astro](https://astro.build/) and deployed to [Cloudflare Pages](https://pages.cloudflare.com/).

```bash
npm install
npm run dev      # Local dev server at localhost:4321
npm run build    # Build to ./dist
npm run preview  # Preview production build
```

## Deployment

Merging to `main` triggers an automatic build and deploy to Cloudflare Pages. The site publishes to [ai.shakacode.com](https://ai.shakacode.com).

**Cloudflare Pages settings:**
- Build command: `npm run build`
- Build output directory: `dist`
- Node.js version: 22

## About ShakaCode

[ShakaCode](https://shakacode.com) is a consultancy specializing in AI-augmented Ruby on Rails and React development. We're the company behind [React on Rails](https://github.com/shakacode/react_on_rails) and the ShakaCode open-source ecosystem.

If your team is navigating AI-assisted development and could use experienced partners, [reach out](https://shakacode.com).
