---
marp: true
theme: default
paginate: true
title: "Agentic SDLC with GitHub — Royal Caribbean Enablement"
footer: "GitHub Solutions Engineering — March 19, 2026"
---

# Agentic SDLC with GitHub

## Royal Caribbean Enablement & Demo Session

*From Planning to Production — AI-Powered at Every Phase*

---

# Agenda

| Time | Block |
|------|-------|
| 5 min | Overview & Introductions |
| **60 min** | **Deep Dive Demos** |
| 20 min | Q&A |
| 5 min | Enablement Workshop Draft Review |

---

# Your SDLC, Supercharged

We'll follow **your** development lifecycle and show how GitHub Copilot and the GitHub platform enhance each phase.

```
Initiation / Planning  →  Build  →  Test / QA  →  Secure  →  Deliver / Govern
       Jira + Copilot       VS Code    Playwright    GHAS       CI/CD + Dashboards
```

> Everything demoed today works with the tools you already use.

---

# Part 1 — Copilot Extensibility

## Custom Instructions · Custom Agents · Skills · MCP

*The building blocks that make Copilot yours*

---

# 📋 Custom Instructions

## Persistent rules Copilot always follows

- **Repo-wide:** `.github/copilot-instructions.md`
- **Path-specific:** `.instructions.md` files (e.g., frontend vs. backend)

### Why RCCL cares

- Enforce coding standards across squads
- Embed security requirements into every suggestion
- New developers get guardrails from day one

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
- Write Playwright tests for all new UI features
- Minimum 80% coverage for new code
```

---

# 🤖 Coding Agent

## AI teammate that works autonomously

1. Assign a GitHub Issue to **@copilot**
2. Agent spins up a secure cloud environment
3. Reads repo context, instructions, and issue details
4. Makes code changes across multiple files
5. Runs your CI pipeline (build, test, lint)
6. Opens a **draft PR** for human review
7. Iterates on review feedback

**Key:** Agent cannot merge — **human review is always required**.

---

# 🤖 Custom Agents

## Specialized AI personas for your team

- Defined in `.github/agents/*.agent.md`
- Each agent has its own instructions, tools, and guardrails
- Examples: Security Reviewer, Docs Writer, Migration Specialist

### Relevant for RCCL

- **QA Agent** — runs Playwright tests and reports results
- **Security Agent** — checks for vulnerabilities before merge
- **Onboarding Agent** — helps new devs ramp up with team conventions

---

# 🧩 Skills

## Reusable task playbooks for Copilot

- Stored in `.github/skills/*/SKILL.md`
- Auto-loaded when a prompt matches the skill description
- Step-by-step instructions, scripts, templates

### How Skills differ from Instructions

| Instructions | Skills |
|---|---|
| Always on | On-demand |
| Rules & standards | Procedures & workflows |
| "Always do this" | "Here's how to do this specific thing" |

> Package your team's tribal knowledge into shareable, reusable units.

---

# 🔌 MCP (Model Context Protocol)

## Universal protocol for AI ↔ tool communication

- Open standard — Copilot is the **client**, external tools are **servers**
- Copilot discovers tools, invokes actions, retrieves data

### MCP servers relevant to RCCL

| Category | Examples |
|----------|----------|
| **GitHub** | PRs, Issues, Actions, Code Search |
| **Testing** | Playwright |
| **DevOps** | Docker, Kubernetes, Terraform |
| **Custom** | Your internal APIs and tools |

> **Analogy:** USB-C for AI integrations — one standard, every tool

---

# 🎭 Part 2 — Playwright MCP in Action

## AI-driven end-to-end testing

**Live Demo:** Using Copilot + Playwright MCP to:

1. Ask Copilot to navigate to a web application
2. Copilot drives the browser via MCP — clicks, fills forms, takes screenshots
3. Copilot validates expected behavior and reports results
4. Generate Playwright test scripts from natural language descriptions

> **For RCCL:** Accelerate QA testing for booking flows, loyalty portals, and crew management apps.

---

# Part 3 — Coding Agent & Code Review

## From issue to reviewed PR — hands-free

---

# Coding Agent — Demo Flow

**Live Demo:**

1. **Create an issue** describing a feature or bug fix
2. **Assign to @copilot** — agent picks it up automatically
3. Watch the agent:
   - Analyze the codebase
   - Write code changes and tests
   - Run CI pipeline
4. **Review the draft PR** — Copilot Code Review provides AI-powered feedback
5. **Iterate** — push review comments, agent responds with fixes

> Agent + Code Review = quality code with minimal manual effort.

---

# Copilot Code Review

## AI-powered pull request reviews

- Automatically triggered on PR creation (or on-demand)
- Reviews for correctness, security, performance, and style
- Inline suggestions that can be committed with one click
- Respects your Custom Instructions for team-specific standards

### What RCCL gets

- Faster PR turnaround — no waiting for human reviewers
- Consistent review quality across all squads
- Security issues caught before they reach main

---

# Part 4 — Assigning Work & Iterating

## The Agentic workflow loop

---

# The Assign → Build → Review → Iterate Loop

```
┌──────────────────────────────────────────────┐
│  1. Create Issue (GitHub or Jira-linked)     │
│         │                                    │
│  2. Assign to @copilot                       │
│         │                                    │
│  3. Agent builds code + tests                │
│         │                                    │
│  4. CI runs (Actions, linters, Playwright)   │
│         │                                    │
│  5. Draft PR opened                          │
│         │                                    │
│  6. Human reviews, leaves comments           │
│         │                                    │
│  7. Agent iterates on feedback               │
│         │                                    │
│  8. Human approves & merges ✅               │
└──────────────────────────────────────────────┘
```

> **Multiple issues can run in parallel** — scale your team with agents.

---

# Part 5 — Jira Integration with Copilot

## Bridging project management and development

---

# Jira + GitHub — Seamless Workflow

**Live Demo:**

- Link Jira issues to GitHub PRs and branches
- Copilot reads Jira context (story, acceptance criteria, subtasks)
- Agent uses Jira details to inform code generation
- Status syncs: PR merged → Jira issue transitions

### Why this matters for RCCL

- **No workflow change** — keep using Jira for planning
- **Richer context** — Copilot understands your requirements, not just your code
- **Traceability** — every code change links back to a Jira story

---

# Part 6 — GitHub Advanced Security (GHAS)

## Security as a value-add alongside Snyk

---

# GHAS: What You Get

| Capability | What it does |
|---|---|
| **Code Scanning (CodeQL)** | Finds vulnerabilities in source code |
| **Copilot Autofix** | AI generates fix PRs for security alerts |
| **Secret Scanning** | Detects exposed credentials and tokens |
| **Push Protection** | Blocks secrets **before** they're committed |
| **Dependabot** | Alerts + auto-PRs for vulnerable dependencies |
| **Security Overview** | Org-wide dashboard for risk visibility |

---

# 🔧 Copilot Autofix — Demo

## AI-generated security fixes

**Live Demo:**

1. Code scanning finds a SQL injection vulnerability
2. Copilot Autofix generates a fix — shows the diff
3. Developer reviews and merges the fix PR with one click

### For RCCL

- Reduces mean-time-to-remediate from **days to minutes**
- Developers learn secure coding patterns from the fix suggestions
- Complements Snyk with deeper, AI-powered remediation

---

# 🔒 Secret Push Protection — Demo

## Stop leaked secrets before they reach the repo

**Live Demo:**

1. Developer attempts to commit an AWS key
2. Push protection **blocks the push** with a clear message
3. Options: remove secret, mark as test, request bypass
4. Delegated bypass routes to security team for approval

### For RCCL

- Works alongside **PAM & AWS Secrets Manager**
- Prevents the need for credential rotation after a leak
- Custom patterns can match RCCL-specific secret formats

---

# Part 7 — Mission Control & Dashboards

## Visibility, auditability, and reporting

---

# Copilot Dashboard & Metrics

## Understand adoption and impact

- **Copilot Metrics API** — acceptance rates, languages, editors
- **Usage dashboard** — who's using Copilot, how often, where
- **Seat management** — optimize license allocation

### Reporting for RCCL leadership

- Export data to Excel / integrate with MSFT reporting
- Track developer productivity trends over time
- Quantify ROI: time saved, PRs accelerated, vulnerabilities caught

---

# Security Overview & Audit

## Enterprise-wide risk visibility

- **Security Overview dashboard** — risk posture across all repos
- **Alert trends** — open vs. closed over time, MTTR
- **Coverage views** — which repos have scanning enabled
- **Audit log** — every action tracked for compliance

### For RCCL

- Single pane of glass for security leadership
- Supports compliance requirements (SOC 2, PCI)
- Exportable reports for governance reviews

---

# Part 8 — Governance & Guardrails

## Control without slowing developers

---

# Governance Built Into the Platform

| Guardrail | How it works |
|---|---|
| **Rulesets** | Branch protection, required reviews, status checks |
| **Custom Instructions** | Enforce coding standards via AI |
| **Policy-as-Code** | Organization-level rules applied across all repos |
| **Copilot Content Exclusion** | Block specific files/repos from Copilot suggestions |
| **MCP Governance** | Admin-controlled MCP server allowlists |
| **Audit Log Streaming** | Ship audit data to Splunk, Datadog, or SIEM |

> **Key message:** Developers stay fast. Leadership stays informed. Security stays enforced.

---

# How It All Fits Together

```
┌─────────────────────────────────────────────────────┐
│                  GitHub Platform                     │
│                                                     │
│  Initiation        Build           Test             │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐      │
│  │  Jira ↔  │    │ Copilot  │    │Playwright│      │
│  │  GitHub   │───▶│ Coding   │───▶│  MCP +   │      │
│  │  Issues   │    │ Agent    │    │  QA Agent│      │
│  └──────────┘    └──────────┘    └──────────┘      │
│       │               │               │             │
│       ▼               ▼               ▼             │
│  Secure            Deliver          Govern          │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐      │
│  │  GHAS    │    │  CI/CD   │    │ Rulesets  │      │
│  │ Autofix  │───▶│ Actions  │───▶│ Audit Log │      │
│  │ Push Prot│    │Dashboard │    │ Policy    │      │
│  └──────────┘    └──────────┘    └──────────┘      │
└─────────────────────────────────────────────────────┘
```

---

# Key Takeaways

1. **Agentic SDLC is an evolution** — layer AI on your existing tools and workflows
2. **Copilot extensibility** (Instructions, Agents, Skills, MCP) makes AI work *your* way
3. **GHAS complements Snyk** — Autofix and Push Protection add AI-powered security
4. **Governance is built in** — visibility and control without slowing developers
5. **Everything integrates** — Jira, VS Code, Playwright, GitHub, and MSFT reporting

---

# Next Steps

1. **Enablement Workshop** — hands-on session for RCCL developers (draft to review)
2. **Pilot Program** — select 2–3 teams to adopt Coding Agent + Custom Instructions
3. **GHAS Evaluation** — run parallel scan vs. Snyk to compare coverage
4. **Dashboard Setup** — configure Copilot metrics and Security Overview for leadership
5. **Follow-up** — check in 30 days post-enablement for feedback and iteration

---

# Resources

- [Custom Instructions Docs](https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions)
- [Coding Agent Docs](https://docs.github.com/en/copilot/concepts/agents/coding-agent/about-coding-agent)
- [Agent Skills Docs](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills)
- [MCP Docs](https://docs.github.com/en/copilot/concepts/context/mcp)
- [Copilot Spaces Docs](https://docs.github.com/en/copilot/how-tos/provide-context/use-copilot-spaces/use-copilot-spaces)
- [GHAS Overview](https://docs.github.com/en/get-started/learning-about-github/about-github-advanced-security)
- [Playwright MCP](https://github.com/nicolo-ribaudo/playwright-mcp)
- [GitHub Blog: Coding Agent 101](https://github.blog/ai-and-ml/github-copilot/github-copilot-coding-agent-101-getting-started-with-agentic-workflows-on-github/)

---

# Thank You

**Questions?**

*GitHub Solutions Engineering*
