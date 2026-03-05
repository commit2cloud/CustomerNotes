---
marp: true
theme: default
paginate: true
title: "GitHub Copilot: Instructions, Agents, Skills, Spaces & MCP"
footer: "GitHub Solutions Engineering"
---

# GitHub Copilot Extensibility

## Instructions, Agents, Skills, Spaces & MCP

*When and where to use each*

---

# The Landscape

Copilot is not just autocomplete — it's a **customizable, extensible AI platform**.

Five key capabilities let you tailor Copilot to your team:

| | Feature | One-Liner |
|---|---------|-----------|
| 📋 | **Instructions** | Always-on coding rules |
| 🤖 | **Agents** | Autonomous AI teammates |
| 🧩 | **Skills** | Reusable task playbooks |
| 🌐 | **Spaces** | Shared knowledge hubs |
| 🔌 | **MCP** | External tool connections |

---

# 📋 Copilot Instructions

## What: Persistent rules Copilot always follows

- `.github/copilot-instructions.md` → repo-wide
- `.instructions.md` files → path-specific (e.g., frontend vs. backend)
- YAML frontmatter defines which files each instruction applies to

## When to use

- Enforce coding standards and naming conventions
- Set security requirements for every suggestion
- Define architecture guidelines and forbidden patterns

> **Analogy:** Company policy — always in effect, everyone follows it

---

# 📋 Instructions — Example

```markdown
# .github/copilot-instructions.md

## Code Style
- Use camelCase for variables, PascalCase for components
- Always use TypeScript strict mode
- Prefer async/await over .then() chains

## Security
- Set httpOnly, secure, sameSite on all cookies
- Validate all external input with zod schemas

## Testing
- Write Jest tests for all new functions
- Minimum 80% coverage for new code
```

---

# 🤖 Copilot Agents

## Two types

### Coding Agent (built-in)
- Assign a GitHub Issue to `@copilot`
- Agent works autonomously in the cloud
- Opens a draft PR with changes, tests, and CI results
- Iterates on PR feedback

### Custom Agents (user-defined)
- `.github/agents/*.agent.md` files
- Specialized personas: Security Reviewer, Docs Writer, etc.
- Each has its own instructions, tools, and guardrails

> **Analogy:** Junior developer on your team (coding agent) or specialist consultant (custom agent)

---

# 🤖 Coding Agent — How It Works

```
1. Developer assigns issue to @copilot
           │
2. Agent spins up secure environment
           │
3. Reads repo context, issues, discussions
           │
4. Makes code changes across files
           │
5. Runs CI pipeline (build, test, lint)
           │
6. Opens draft PR for human review
           │
7. Iterates on review feedback
           │
8. Human approves and merges ✅
```

**Key:** Agent cannot merge — human review is always required.

---

# 🧩 Copilot Skills

## What: Reusable, modular task playbooks

- Stored in `.github/skills/*/SKILL.md`
- Auto-loaded when a user's prompt matches the skill description
- Step-by-step instructions, scripts, templates, and examples

## When to use

- Standardize repeatable workflows (test generation, CI debugging)
- Package tribal knowledge into shareable units
- Teach Copilot project-specific procedures

## How Skills differ from Instructions

| Instructions | Skills |
|---|---|
| Always on | On-demand |
| Rules & standards | Procedures & workflows |
| "Always do this" | "Here's how to do this specific thing" |

---

# 🌐 Copilot Spaces

## What: Persistent, collaborative knowledge hubs

- Aggregate code, docs, specs, and instructions in one place
- Copilot Chat grounded in all attached context
- Shareable with team, org, or publicly
- Always up-to-date as source repos change
- Replaces deprecated Copilot Knowledge Bases

## When to use

- Onboard new team members with shared context
- Preserve institutional knowledge and design decisions
- Ensure consistent AI responses across a project team
- Run demos or workshops with pre-loaded context

> **Analogy:** Team wiki that Copilot has memorized

---

# 🔌 MCP (Model Context Protocol)

## What: Universal protocol for AI ↔ tool communication

- Open standard (JSON-RPC over HTTP/WebSocket)
- Copilot = MCP client, external tools = MCP servers
- Copilot discovers tools, invokes actions, retrieves data

## Available MCP servers

| Category | Examples |
|----------|----------|
| GitHub | PRs, Issues, Actions, Code Search |
| Design | Figma |
| Databases | PostgreSQL, MongoDB |
| DevOps | Docker, Kubernetes, Terraform |
| Custom | Your internal tools and APIs |

> **Analogy:** USB-C for AI integrations — one standard, every tool

---

# How They Work Together

```
┌─────────────────────────────────────────────┐
│              Copilot Spaces                 │
│        (shared context & knowledge)         │
│                                             │
│  ┌──────────────┐  ┌────────────────────┐   │
│  │ Instructions │  │   MCP Servers      │   │
│  │ (always-on   │  │ (external tools)   │   │
│  │  rules)      │  │                    │   │
│  └──────┬───────┘  └────────┬───────────┘   │
│         │                   │               │
│         ▼                   ▼               │
│  ┌──────────────────────────────────────┐   │
│  │           Copilot Agents             │   │
│  │   (autonomous task execution)        │   │
│  │    ┌────────────────────────────┐    │   │
│  │    │      Copilot Skills        │    │   │
│  │    │  (reusable procedures)     │    │   │
│  │    └────────────────────────────┘    │   │
│  └──────────────────────────────────────┘   │
└─────────────────────────────────────────────┘
```

---

# Comparison At a Glance

| | Instructions | Agents | Skills | Spaces | MCP |
|---|---|---|---|---|---|
| **Purpose** | Rules | Execution | Procedures | Knowledge | Connectivity |
| **When active** | Always | On assignment | On-demand | When attached | When configured |
| **Who creates** | Dev leads | GitHub / devs | Dev leads | Anyone | Platform teams |
| **Requires code** | No | No / Yes | No | No | Yes |
| **Shareable** | Via repo | Via repo | Via repo | Org / public | Across projects |

---

# Decision Guide

| Customer says... | Recommend |
|---|---|
| "We need consistent code quality" | **Instructions** |
| "We want AI to handle routine tasks" | **Coding Agent** |
| "Different teams need different AI behavior" | **Custom Agents** |
| "We have procedures we want AI to follow" | **Skills** |
| "We need shared project knowledge for AI" | **Spaces** |
| "We need Copilot to use our internal tools" | **MCP** |
| "All of the above" | **Combine them — they're complementary layers** |

---

# Common Recipes

### 🏢 Enterprise Consistency
**Instructions** + **Spaces** → Standards enforced, context shared

### ⚡ Automate the Boring Stuff
**Coding Agent** + **Skills** → Autonomous work, standardized procedures

### 🔒 Security-First Development
**Custom Agent** + **Skills** + **MCP** → Specialized reviewer, audit playbooks, scanner integration

### 🚀 Fast Onboarding
**Spaces** + **Instructions** + **Skills** → Shared context, team rules, guided procedures

---

# Key Takeaway

These features are **complementary layers**, not competing alternatives.

| Layer | Feature | Purpose |
|-------|---------|---------|
| 🏗️ Foundation | Instructions | Set the rules |
| 📚 Knowledge | Spaces | Provide shared context |
| 🔌 Connectivity | MCP | Bridge to external tools |
| 🧩 Expertise | Skills | Package reusable know-how |
| 🚀 Execution | Agents | Do the work |

> **Start with Instructions. Add Spaces for context. Connect tools with MCP. Package expertise as Skills. Let Agents execute.**

---

# Resources

- [GitHub Docs: Custom Instructions](https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions)
- [GitHub Docs: Coding Agent](https://docs.github.com/en/copilot/concepts/agents/coding-agent/about-coding-agent)
- [GitHub Docs: Agent Skills](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills)
- [GitHub Docs: Copilot Spaces](https://docs.github.com/en/copilot/how-tos/provide-context/use-copilot-spaces/use-copilot-spaces)
- [GitHub Docs: MCP](https://docs.github.com/en/copilot/concepts/context/mcp)
- [GitHub Blog: Coding Agent 101](https://github.blog/ai-and-ml/github-copilot/github-copilot-coding-agent-101-getting-started-with-agentic-workflows-on-github/)
- [GitHub Blog: 5 ways to use MCP](https://github.blog/ai-and-ml/github-copilot/5-ways-to-transform-your-workflow-using-github-copilot-and-mcp/)

---

# Thank You

**Questions?**

*GitHub Solutions Engineering*
