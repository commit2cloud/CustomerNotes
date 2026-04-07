# Copilot Agentic Workflows — Lunch & Learn Demo Session

> **Duration:** 20–30 minutes &nbsp;|&nbsp; **Format:** Live demos + discussion &nbsp;|&nbsp; **Audience:** Engineering teams exploring AI-assisted development

## Synopsis

GitHub Copilot has evolved from code completion into a suite of **agentic capabilities** — AI that doesn't just suggest code, but takes action across the entire software development lifecycle. In this session we'll walk through the key building blocks, see them in action on a real codebase, and discuss how they fit into your team's workflow.

**What you'll see:**

- **Coding Agent** — Assign a GitHub issue to Copilot and watch it plan, code, test, and open a pull request autonomously in the cloud.
- **Copilot Code Review** — An AI-powered first-pass reviewer that catches bugs and suggests improvements before your human reviewers look at a PR.
- **GitHub Agentic Workflows** — Write repository automations in plain Markdown. Describe your intent, and an AI agent executes it — issue triage, CI failure analysis, doc maintenance, and more.
- **Copilot CLI & Fleet** — Terminal-first agentic coding, plus the ability to fan out parallel sub-agents for multi-part tasks.
- **The broader ecosystem** — Community tools like [Squad](https://github.com/bradygaster/squad) that add multi-agent orchestration on top of Copilot.

**Key takeaway:** Agents handle the heavy lifting; your team stays in the loop for every decision. Nothing ships without human review.

---

> **Prepared by:** Solutions Engineering (@commit2cloud)  
> **Demo App:** [octodemo/octocat_supply](https://github.com/octodemo/octocat_supply) (bootstrapped via [issue template](https://github.com/octodemo/bootstrap/issues/new?template=001_octocat_supply.yml))

---

## Session Agenda (28 min)

| Time | Segment | Focus |
|------|---------|-------|
| 3 min | What Are Agentic Workflows? | Level-set for the room — sync vs async, where agents fit in the SDLC |
| 5 min | Coding Agent (Async) | Assign an issue → agent codes → opens a PR |
| 5 min | Copilot Code Review | AI-powered review on the agent's PR |
| 5 min | GitHub Agentic Workflows (gh-aw) | Markdown-authored, event-driven repo automation via AI agents |
| 5 min | Copilot CLI & Fleet Mode | Terminal-based agentic coding + parallel sub-agents |
| 3 min | Squad & the Agentic Ecosystem | Community tools that extend Copilot's reach |
| 2 min | Wrap-Up & Q&A | Recap + open discussion |

---

## Presenter Notes *(internal — do not share)*

### Contents

| Document | Purpose |
|----------|---------|
| [Demo Script](demo-script.md) | Step-by-step walk-through with talk track, transitions, and live-demo instructions |

---

### Key Messaging

1. **Agentic ≠ autopilot** — humans stay in the loop at every decision point.
2. **Sync + Async = full coverage** — Agent Mode for real-time pairing; Coding Agent for background work; CLI for terminal-first developers.
3. **GitHub Agentic Workflows = Continuous AI** — Markdown-authored, event-driven repo automation that complements CI/CD.
4. **Fleet scales the pattern** — one prompt, many parallel agents, coordinated results.
5. **Ecosystem is growing** — tools like Squad show how the community is building on top of Copilot's agentic capabilities.

---

### Pre-Session Checklist

- [ ] Fork or clone [octodemo/octocat_supply](https://github.com/octodemo/octocat_supply) into your demo org
- [ ] Create a well-scoped issue ready to assign to `@copilot` (e.g., "Add a discount code field to the checkout page")
- [ ] Pre-run the Coding Agent on that issue so a draft PR exists (for smooth demo pacing)
- [ ] Have a second PR with Copilot Code Review comments already visible
- [ ] Install Copilot CLI (`gh extension install github/gh-copilot` or `brew install gh-copilot`)
- [ ] Install the `gh aw` CLI extension and have a sample `.md` workflow ready in `.github/workflows/`
- [ ] Compile the sample agentic workflow: `gh aw compile`
- [ ] Verify `/fleet` works locally: `copilot -p "/fleet hello world" --no-ask-user`
- [ ] Install Squad CLI: `npm install -g @bradygaster/squad-cli` and run `squad init` in the demo repo
- [ ] Browser tabs open: demo repo (Issues, PRs), Copilot CLI terminal, Squad README
