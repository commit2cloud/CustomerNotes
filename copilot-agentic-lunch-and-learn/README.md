# Copilot Agentic Workflows — Lunch & Learn Demo Session

> **Session Duration:** 20–30 minutes  
> **Prepared by:** Solutions Engineering (@commit2cloud)  
> **Format:** Live demos in browser + terminal, with talk-track narration  
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

## Contents

| Document | Purpose |
|----------|---------|
| [Demo Script](demo-script.md) | Step-by-step walk-through with talk track, transitions, and live-demo instructions |

---

## Key Messaging

1. **Agentic ≠ autopilot** — humans stay in the loop at every decision point.
2. **Sync + Async = full coverage** — Agent Mode for real-time pairing; Coding Agent for background work; CLI for terminal-first developers.
3. **GitHub Agentic Workflows = Continuous AI** — Markdown-authored, event-driven repo automation that complements CI/CD.
4. **Fleet scales the pattern** — one prompt, many parallel agents, coordinated results.
5. **Ecosystem is growing** — tools like Squad show how the community is building on top of Copilot's agentic capabilities.

---

## Pre-Session Checklist

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
