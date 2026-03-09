# Royal Caribbean (RCCL) — Agentic SDLC Enablement & Demo Session

> **Customer:** Royal Caribbean Group (RCCL)  
> **Session Date:** March 19, 2026  
> **Prepared by:** Solutions Engineering (@commit2cloud)  
> **Internal Contact:** Kenny (Overview), @commit2cloud (Deep Dive Demos)

---

## Session Agenda (90 min)

| Time | Block | Owner |
|------|-------|-------|
| 5 min | Overview & Introductions | Kenny |
| 60 min | Deep Dive Demos (see below) | @commit2cloud |
| 20 min | Q&A — Open Discussion | All |
| 5 min | Review Enablement Workshop Draft | @commit2cloud |

---

## Demo Flow (60 min)

The demo is structured to follow RCCL's SDLC phases — **Initiation → Build → Test → Secure → Deliver** — and maps every topic to tools RCCL already uses.

| # | Demo Segment | Time | SDLC Phase | RCCL Tools Touched |
|---|---|---|---|---|
| 1 | Custom Instructions, Custom Agents, Skills & MCP | 12 min | Foundation / All | VS Code, Copilot |
| 2 | Playwright MCP in Action | 5 min | QA / Test | Playwright, VS Code |
| 3 | Coding Agent & Code Review | 10 min | Build | GitHub, VS Code, Copilot |
| 4 | Assigning Work & Iterating to Completion | 8 min | Initiation / Build | Jira, GitHub Issues |
| 5 | Jira Integration with Copilot | 5 min | Initiation / Planning | Jira |
| 6 | GHAS: Autofix & Secret Push Protection | 10 min | Secure | Snyk comparison, PAM, AWS Secrets Manager |
| 7 | Mission Control, Auditability & Dashboards | 7 min | Deliver / Govern | GitHub, MSFT reporting |
| 8 | Governance & Guardrails | 3 min | Govern | GitHub |

---

## Contents

| Document | Purpose |
|----------|---------|
| [Slide Deck (Marp)](slide-deck.md) | Customer-facing presentation — render with [Marp](https://marp.app) |
| [Demo Script](demo-script.md) | Step-by-step script with talking points, transitions, and live-demo instructions |

---

## RCCL Context & Tool Stack

| Category | Tools |
|----------|-------|
| Project Management | Jira (initiation, bugs, sprint planning) |
| Productivity | Microsoft Excel, Docs, Teams |
| IDE | VS Code (primary) |
| AI | GitHub Copilot (central) |
| Testing | Playwright (exploring) |
| SAST | Snyk |
| Secrets | PAM, AWS Secrets Manager |
| Security | GHAS not currently in stack — demo as value-add |

---

## Key Messaging

1. **Meet RCCL where they are** — everything demoed works with Jira, VS Code, and Playwright today.
2. **Agentic SDLC is an evolution, not a migration** — layer Copilot capabilities on top of existing workflows.
3. **GHAS as a value-add** — position Autofix and Push Protection as complements to Snyk, not replacements.
4. **Governance built in** — Mission Control, audit logs, and policy-as-code give leadership visibility without slowing developers.

---

## Pre-Session Checklist

- [ ] Confirm attendee list and roles with Kenny
- [ ] Verify Jira integration demo environment is accessible
- [ ] Prepare sample repo with Custom Instructions, Agents, Skills, and MCP configured
- [ ] Confirm Playwright MCP server is running for live demo
- [ ] Seed sample security alerts (code scanning + secret scanning) in demo repo
- [ ] Test dashboard / Security Overview views in demo org
- [ ] Print or share one-pager leave-behind (link to enablement workshop draft)
- [ ] Gather feedback from RCCL stakeholders on priorities ahead of session

_Linked for context: [GH panam account plan comment](https://github.com/github/panam/issues/179#issuecomment-3993513371)_
