# Copilot Agentic Workflows — Lunch & Learn Demo Script

> **Session Duration:** 20–30 minutes  
> **Presenter:** @commit2cloud  
> **Demo App:** [octodemo/octocat_supply](https://github.com/octodemo/octocat_supply)  
> **Audience:** New to agentic workflows — assume no prior context on AI agents in development

---

## Segment 1 — What Are Agentic Workflows? (3 min)

### Goal

Level-set the room on what "agentic" means in the context of software development, and frame the rest of the session.

### Talking Points

> "Before we jump into demos, let me set the stage. When we talk about **agentic workflows**, we mean AI that doesn't just suggest a line of code — it takes action. It reads your issue, plans a solution, writes code, runs your tests, and opens a pull request. It's the difference between autocomplete and a teammate."

**Two modes to know:**

| Mode | How It Works | When to Use It |
|------|-------------|---------------|
| **Synchronous (Agent Mode)** | Real-time in your IDE — you watch, guide, and course-correct as Copilot works | Prototyping, pair programming, exploratory coding |
| **Asynchronous (Coding Agent)** | Background in the cloud — assign an issue, walk away, come back to a PR | Well-scoped tasks, sprint backlog items, maintenance |

> "Think of sync as pair programming and async as delegating to a junior developer. Today I'll show you both — plus how the CLI and community tools like Squad extend the pattern even further."

### Transition

> "Let's start with the async side — the Coding Agent."

---

## Segment 2 — Coding Agent: Issue → PR (5 min)

### Goal

Demonstrate the full async loop: assign an issue to Copilot, the agent works autonomously, and a PR appears.

### Demo Steps

**Show the Issue (1 min)**

1. Open the demo repo on GitHub → **Issues** tab
2. Show a pre-created issue: *"Add a discount code field to the checkout page"*
3. Point out: clear title, description with acceptance criteria, labels

> **Talking point:** "Good issues make good agents. The more context you put into the issue — acceptance criteria, links, constraints — the better the result. This is true for human developers too, right?"

**Assign to Copilot (1 min)**

4. Click **Assignees** → select `@copilot`
5. Show the status banner: *"Copilot is working on this issue…"*
6. Explain what's happening behind the scenes:

> "The agent spins up a secure sandboxed environment via GitHub Actions. It reads your repo — code, tests, custom instructions, CI config — builds a plan, and starts coding. No local machine needed."

**Review the PR (3 min)**

7. Switch to the **Pull Requests** tab → open the draft PR the agent created (pre-prepared)
8. Walk through the changes:
   - New component or field added
   - Tests written
   - CI pipeline passing (green checks)
9. Show the agent's session log (the summary comment on the PR)

> **Talking point:** "Notice three things: it followed the repo's coding patterns, it wrote tests, and CI is green. The agent didn't just generate code — it validated its own work. But it's still a *draft* PR. Nothing merges without a human."

**Show the Iteration Loop**

10. Leave a review comment: *"Please also add input validation for the discount code format"*
11. Point out: "The agent picks this up and pushes another commit. It's a conversation — just like working with a teammate on a PR."

### Transition

> "So the agent wrote the code. But who reviews it? Let's talk about Copilot Code Review."

---

## Segment 3 — Copilot Code Review (5 min)

### Goal

Show how Copilot can act as a first-pass reviewer on any pull request — catching bugs, suggesting improvements, and accelerating the review cycle.

### Talking Points

> "Code review is where most teams hit a bottleneck. PRs sit for hours or days waiting for a reviewer. Copilot Code Review doesn't replace your human reviewers — it gives them a head start."

### Demo Steps

**Request a Review (1 min)**

1. On the agent's PR (or a second pre-prepared PR), click **Reviewers** → add **Copilot**
2. Wait ~30 seconds — Copilot analyzes the diff and surrounding code context

> **Talking point:** "Copilot reads the full diff plus the surrounding code — not just the changed lines. Since the recent agentic architecture update, it explores related files and cross-file dependencies too."

**Walk Through the Feedback (3 min)**

3. Show Copilot's inline comments:
   - A potential bug (e.g., missing null check)
   - A style suggestion
   - A one-click suggested fix
4. Click **"Commit suggestion"** on one of the suggestions — show the fix applied instantly
5. Point out the review type: *"Comment"* — not Approve or Request Changes

> **Talking point:** "Copilot reviews are always 'Comment' type — they never block a merge or count toward required approvals. Your team's approval rules stay exactly as they are. Think of it as an AI first-pass that catches the low-hanging fruit so your human reviewers can focus on architecture and design."

**Mention the CLI Path (1 min)**

6. Briefly mention: "You can also trigger Code Review from the Copilot CLI with `/review` — same analysis, same suggestions, right from your terminal."

### Transition

> "Speaking of the terminal — let me show you the Copilot CLI and a feature called Fleet."

---

## Segment 4 — Copilot CLI & Fleet Mode (7 min)

### Goal

Introduce the Copilot CLI as a terminal-first agentic tool, then demonstrate Fleet mode for parallel sub-agent execution.

### Talking Points

> "Not everyone lives in the IDE. For terminal-first developers — and for automation scripts — Copilot CLI brings the same agentic capabilities right to your command line."

### Demo Steps

**Copilot CLI Basics (2 min)**

1. Open a terminal in the demo repo directory
2. Run a simple prompt:
   ```bash
   copilot -p "Explain the architecture of this project"
   ```
3. Show Copilot analyzing the repo and producing a structured response
4. Run a coding task:
   ```bash
   copilot -p "Add a health check endpoint to the API" --autopilot
   ```
5. Briefly show the agent working: reading files, editing, running tests

> **Talking point:** "Same agentic loop as the Coding Agent, but local and synchronous. You watch it work in real time. The `--autopilot` flag lets it run without asking for approval at each step — great for well-defined tasks."

**Fleet Mode — Parallel Agents (5 min)**

6. Explain the concept:

> "What if your task has multiple independent parts? Instead of doing them one by one, Fleet decomposes your prompt into sub-tasks and dispatches parallel agents."

7. Run a fleet command:
   ```bash
   copilot -p "/fleet Update the README with the new API endpoints, add JSDoc comments to all exported functions in api/routes/, and generate missing unit tests for the discount module" --no-ask-user
   ```
8. Show the orchestrator output:
   - Task decomposition (3 sub-tasks identified)
   - Dependency analysis (these are independent → run in parallel)
   - Parallel dispatch (agents working simultaneously)
   - Results converging

> **Talking point:** "Fleet is like having a small team on call. You describe the work, the orchestrator figures out what can run in parallel, and each sub-agent handles its piece. When they're done, Fleet integrates the results."

9. Show the final output — all three changes applied

**Key Flags to Mention**

| Flag | What It Does |
|------|-------------|
| `--autopilot` | No approval prompts — fully autonomous |
| `--no-ask-user` | Skip all interactive prompts |
| `/fleet` | Trigger parallel sub-agent decomposition |

> **Talking point:** "CLI + Fleet is where async meets scale. Imagine running this in CI, in a cron job, or as part of a migration script. That's the direction the ecosystem is heading."

### Transition

> "And the ecosystem *is* heading there — fast. Let me show you one community project that takes this even further."

---

## Segment 5 — Squad & the Agentic Ecosystem (3 min)

### Goal

Introduce Squad as an example of community-built tooling on top of Copilot's agentic capabilities, and give the audience a sense of where the ecosystem is going.

### Talking Points

> "Agentic workflows don't stop at what GitHub ships out of the box. The community is building on top of these capabilities. Let me show you one of the most interesting projects: **Squad**."

### Demo Steps

**What Is Squad? (1 min)**

1. Open [github.com/bradygaster/squad](https://github.com/bradygaster/squad) in the browser
2. Quick overview:

> "Squad gives you a *team* of AI specialists — frontend, backend, tester, lead — that live in your repo as configuration files. Each agent has its own context, its own knowledge, and writes back what it learned. It's not one AI wearing different hats — each team member runs independently."

**Show the Setup (1 min)**

3. Show the `.squad/team.md` file in a demo repo (or the Squad README)
4. Highlight key concepts:
   - Persistent team members with themed names
   - Decision archive — the team remembers past choices
   - Watch mode — Ralph (the triage agent) polls for issues and dispatches agents autonomously

> **Talking point:** "Squad takes the Coding Agent pattern and adds orchestration, memory, and specialization. It's a glimpse of where multi-agent development is heading."

**The Bigger Picture (1 min)**

5. Briefly mention the broader ecosystem:

> "Squad is one example. The pattern we're seeing is:
> - **GitHub ships the primitives** — Coding Agent, CLI, Fleet, Code Review, MCP
> - **The community builds the orchestration** — Squad, custom agents, workflow automation
> - **Your team customizes for your context** — Custom Instructions, Skills, MCP servers
>
> It's layers. You adopt what makes sense for your team today, and the platform grows with you."

### Transition

> "Let me wrap up with a quick recap."

---

## Segment 6 — Wrap-Up & Q&A (2 min)

### Closing Summary

> "Here's what we covered in the last 25 minutes:
>
> | What | Why It Matters |
> |------|---------------|
> | **Agentic Workflows** | AI that takes action, not just suggests — sync for pairing, async for delegation |
> | **Coding Agent** | Assign an issue, get a PR — autonomous coding in the cloud |
> | **Code Review** | AI first-pass review that accelerates your team's review cycle |
> | **Copilot CLI + Fleet** | Terminal-first agentic coding with parallel sub-agent execution |
> | **Squad & Ecosystem** | Community tools building multi-agent teams on top of Copilot |
>
> The common thread: **humans stay in the loop**. Agents do the heavy lifting, but your team makes the decisions. No code merges without human approval."

### Open Q&A

> "What questions do you have? Happy to dive deeper into any of these areas."

---

## Q&A Prep — Likely Questions

| Question | Key Points |
|----------|-----------|
| "How do we get started with the Coding Agent?" | Enable it in your org's Copilot settings. Assign any well-scoped issue to `@copilot`. Start with low-risk tasks — docs updates, test coverage, small features. |
| "Is the Coding Agent safe? Can it break production?" | It runs in a sandboxed GitHub Actions environment. All output is a draft PR — nothing merges without human review. Branch protections and required approvals still apply. |
| "What does this cost?" | Coding Agent and Code Review are included with Copilot Business and Enterprise. CLI is available for all paid Copilot plans. Premium requests may apply for heavy usage. |
| "Can we use this with our existing CI/CD?" | Yes — the agent triggers your existing CI workflows. If your tests fail, the agent sees the failure and tries to fix it. Your pipeline doesn't change. |
| "How does Fleet handle conflicts between sub-agents?" | The orchestrator manages dependencies as a DAG. Tasks that depend on each other run sequentially; independent tasks run in parallel. Final integration resolves overlaps. |
| "Is Squad production-ready?" | Squad is alpha software — experimental and evolving. Great for exploration and internal tooling, but evaluate before production use. |
| "What about IP and code privacy?" | Copilot Enterprise: no code used for training, data encrypted in transit and at rest, content exclusions available for sensitive repos. |

---

## Post-Session Follow-Up

- [ ] Share this agenda and any demo recordings with attendees
- [ ] Send relevant links (see below)
- [ ] Offer a deeper hands-on session if the team wants to try the Coding Agent or CLI themselves
- [ ] Check in at 2 weeks for feedback and next steps

## Useful Links

**Agentic Workflows:**
- [From idea to PR: A guide to GitHub Copilot's agentic workflows](https://github.blog/ai-and-ml/github-copilot/from-idea-to-pr-a-guide-to-github-copilots-agentic-workflows/)
- [Coding Agent 101: Getting started](https://github.blog/ai-and-ml/github-copilot/github-copilot-coding-agent-101-getting-started-with-agentic-workflows-on-github/)
- [The difference between coding agent and agent mode](https://github.blog/developer-skills/github/less-todo-more-done-the-difference-between-coding-agent-and-agent-mode-in-github-copilot/)

**Code Review:**
- [Using Copilot Code Review (docs)](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/request-a-code-review/use-code-review)
- [Copilot Code Review now runs on an agentic architecture](https://github.blog/changelog/2026-03-05-copilot-code-review-now-runs-on-an-agentic-architecture/)

**Copilot CLI & Fleet:**
- [Run multiple agents at once with /fleet](https://github.blog/ai-and-ml/github-copilot/run-multiple-agents-at-once-with-fleet-in-copilot-cli/)
- [Running tasks in parallel with /fleet (docs)](https://docs.github.com/en/copilot/concepts/agents/copilot-cli/fleet)

**Squad:**
- [bradygaster/squad on GitHub](https://github.com/bradygaster/squad)

**Demo Repo:**
- [octodemo/octocat_supply](https://github.com/octodemo/octocat_supply)
