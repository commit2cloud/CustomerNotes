# Royal Caribbean — Agentic SDLC Demo Script

> **Session Date:** March 19, 2026  
> **Demo Duration:** 60 minutes  
> **Presenter:** @commit2cloud  
> **Format:** Live demos in VS Code + browser, interspersed with slides

---

## Pre-Demo Setup Checklist

- [ ] Demo repo cloned locally with Custom Instructions, Agents, Skills, and MCP already configured
- [ ] VS Code open with Copilot extension active
- [ ] Playwright MCP server running (`npx @anthropic-ai/mcp-playwright`)
- [ ] Jira demo project with sample stories linked to GitHub repo
- [ ] Demo repo seeded with:
  - A SQL injection vulnerability (for Autofix demo)
  - An AWS secret in a staged commit (for Push Protection demo)
  - A pending issue ready to assign to `@copilot`
- [ ] Browser tabs open: GitHub Security Overview, Copilot Dashboard, demo repo
- [ ] Slides loaded in Marp (backup: PDF export)

---

## Segment 1 — Custom Instructions, Custom Agents, Skills & MCP (12 min)

### Goal
Show RCCL how Copilot can be customized to follow their team's standards, automate work, and connect to external tools.

### Talking Points

> "Copilot is not just autocomplete — it's a customizable, extensible AI platform. Today I'll show you four capabilities that let you make Copilot work the way **your** teams work."

### Demo Steps

**Custom Instructions (3 min)**

1. Open `.github/copilot-instructions.md` in VS Code
2. Show the structure: Code Style, Security, Testing sections
3. **Live:** Ask Copilot to write a function — point out how it follows the instructions (naming, error handling, test patterns)
4. Edit the instructions file (e.g., add "Use Playwright for all UI tests") — show how Copilot immediately adapts

> **Talking point:** "These instructions travel with your repo. Every developer, every branch, every Copilot interaction follows them. Think of it as policy-as-code for AI."

**Custom Agents (3 min)**

5. Open `.github/agents/security-reviewer.agent.md`
6. Walk through the file: persona, instructions, tools available
7. Show how you invoke the agent in Copilot Chat: `@security-reviewer review this PR`
8. Mention the QA Agent concept — "Imagine an agent that runs your Playwright tests and summarizes failures."

> **Talking point:** "Custom agents are specialist consultants on your team. You define their expertise, their tools, and their guardrails."

**Skills (3 min)**

9. Open `.github/skills/generate-tests/SKILL.md`
10. Show the skill structure: description, steps, templates
11. **Live:** Ask Copilot "generate tests for this module" — Copilot auto-loads the skill and follows the playbook
12. Highlight: "Your senior engineers' knowledge, packaged and reusable."

> **Talking point:** "Skills are tribal knowledge made scalable. Instead of your senior dev explaining 'how we write tests here' for the hundredth time, Copilot knows."

**MCP Overview (3 min)**

13. Show `settings.json` or `.vscode/mcp.json` with MCP server configurations
14. List the configured servers: GitHub, Playwright, etc.
15. Brief explanation: "MCP is the universal standard — like USB-C for AI. One protocol, every tool."
16. Transition: "Let me show you MCP in action with Playwright…"

---

## Segment 2 — Playwright MCP in Action (5 min)

### Goal
Show RCCL how Copilot can drive a browser via MCP for QA testing — directly relevant to their Playwright exploration.

### Talking Points

> "I know RCCL is exploring Playwright. Let me show you how Copilot can use Playwright as an MCP tool to automate testing from natural language."

### Demo Steps

1. In Copilot Chat, type: "Navigate to [demo app URL] and verify the login page loads correctly"
2. Copilot invokes the Playwright MCP server — browser opens, navigates, takes a screenshot
3. Copilot reports: "Login page loaded, found username field, password field, and submit button"
4. Follow up: "Fill in the login form with test credentials and submit"
5. Copilot drives the browser — fills fields, clicks submit, reports the result
6. Ask: "Generate a Playwright test script for this login flow"
7. Copilot generates a reusable `.spec.ts` file

> **Talking point:** "Your QA team can describe tests in English. Copilot translates that into Playwright actions and reusable test scripts. Manual test cases become automated tests."

### Transition

> "Now let's look at how all of this comes together when the Coding Agent tackles real work…"

---

## Segment 3 — Coding Agent & Code Review (10 min)

### Goal
Demonstrate the full coding agent lifecycle: issue → code → CI → review → iteration.

### Talking Points

> "The Coding Agent is like a junior developer on your team. You give it a task, it writes code, runs your CI pipeline, and opens a PR for review. Let me show you the full loop."

### Demo Steps

**Assign Work (3 min)**

1. Open the demo repo on GitHub
2. Show a pre-created issue: "Add input validation to the booking API endpoint"
3. Assign the issue to `@copilot`
4. Show the notification: "Copilot is working on this issue…"
5. While waiting, explain: "The agent reads your repo — instructions, code, tests, CI config — and builds a plan."

**Agent Working (3 min)**

6. Switch to the PR that the agent has opened (pre-prepared for demo flow)
7. Walk through the changes:
   - New validation logic added
   - Tests written (following the custom instructions)
   - CI pipeline passed (green checks)
8. Point out: "Notice it followed our custom instructions — TypeScript strict mode, zod validation, Playwright tests."

**Code Review (4 min)**

9. Show Copilot Code Review comments on the PR
10. Highlight an inline suggestion: "Copilot caught a missing error case"
11. Click "Commit suggestion" to apply the fix
12. Show how the agent responds to manual review comments — leave a comment, agent pushes a fix
13. Final: approve and merge

> **Talking point:** "Human in the loop, always. The agent does the heavy lifting, but your team makes the decisions. No code merges without human approval."

### Transition

> "You saw me assign work via a GitHub Issue. But RCCL uses Jira for planning — let me show you how that integrates…"

---

## Segment 4 — Assigning Work & Iterating to Completion (8 min)

### Goal
Show the full iteration loop and how multiple agents can work in parallel.

### Talking Points

> "Agentic SDLC isn't about one task at a time. You can assign multiple issues to Copilot and it works on them in parallel — like scaling your team on demand."

### Demo Steps

1. Show 3 issues in the demo repo, each assigned to `@copilot`
2. Show the resulting 3 draft PRs — all worked on simultaneously
3. Pick one PR and demonstrate the iteration loop:
   - Leave a review comment: "Please add error logging here"
   - Show the agent responding with a new commit
4. Demonstrate re-requesting review after the agent's changes
5. Show the PR checks passing after iteration

> **Talking point:** "Think about sprint planning. Your team identifies 20 tasks. Ten are well-defined enough for the agent. Assign those to Copilot, and your developers focus on the complex, creative work."

**Handling edge cases:**

6. Show what happens when the agent gets stuck:
   - Agent leaves a comment asking for clarification
   - Developer responds, agent picks back up
7. Emphasize: "It's a conversation, not fire-and-forget."

### Transition

> "Now let's talk about where the work originates — Jira…"

---

## Segment 5 — Jira Integration with Copilot (5 min)

### Goal
Show RCCL that their Jira workflow doesn't need to change — GitHub integrates seamlessly.

### Talking Points

> "RCCL uses Jira for product initiation, bugs, enhancements, and sprint planning. That doesn't change. GitHub integrates directly with Jira, and Copilot can read that context."

### Demo Steps

1. Show a Jira story with acceptance criteria, subtasks, and labels
2. Show the linked GitHub branch and PR
3. In VS Code, open Copilot Chat — ask about the Jira story context
4. Demonstrate: "Copilot, based on the Jira story, what tests should I write for this feature?"
5. Show bidirectional sync: PR merged → Jira status transitions automatically

> **Talking point:** "Your PMs stay in Jira. Your developers stay in VS Code. Copilot understands both worlds. And leadership gets traceability from story to deployed code."

### Transition

> "Great — so we've seen the 'build' and 'plan' phases. Now let's talk about security…"

---

## Segment 6 — GHAS: Autofix & Secret Push Protection (10 min)

### Goal
Position GHAS as a complement to Snyk, emphasizing AI-powered remediation and secret prevention that Snyk doesn't offer in the same way.

### Talking Points

> "I know GHAS isn't part of RCCL's current security strategy, and Snyk is handling SAST. What I want to show you are two capabilities that go beyond traditional scanning — AI-powered autofix and pre-commit secret protection."

### Demo Steps

**Copilot Autofix (5 min)**

1. Open the demo repo's Security tab → Code scanning alerts
2. Click on a SQL injection alert
3. Show the alert details: file, line, description, severity
4. Click **"Generate fix"** — Copilot Autofix produces a PR with the fix
5. Walk through the diff: parameterized query replacing string concatenation
6. Show the explanation Autofix provides for the fix
7. Merge the fix

> **Talking point:** "With Snyk, you get the alert and have to figure out the fix. With Copilot Autofix, you get the alert **and** the fix — reviewed and ready to merge. Mean-time-to-remediate goes from days to minutes."

**Secret Push Protection (5 min)**

8. In VS Code terminal, stage a commit containing an AWS access key
9. Attempt `git push` — Push Protection **blocks** the push
10. Show the block message: secret type detected, remediation options
11. Walk through the options: remove, mark as test, request bypass
12. Show the delegated bypass flow: request → security team approves/denies

> **Talking point:** "This works before the secret ever reaches the repo — prevention, not detection. Your PAM and AWS Secrets Manager handle secret storage; Push Protection makes sure developers don't accidentally bypass them."

13. Briefly show: custom secret patterns — "You can define patterns for RCCL-specific credentials or internal tokens."

### Transition

> "Now leadership wants to know: how do we see all of this? What's our risk posture? Let's look at dashboards…"

---

## Segment 7 — Mission Control, Auditability & Dashboards (7 min)

### Goal
Show RCCL leadership that GitHub provides full visibility into Copilot adoption, security posture, and developer activity.

### Talking Points

> "Everything we've demoed today generates data. Let me show you the dashboards that give leadership visibility — without developers having to do anything extra."

### Demo Steps

**Copilot Dashboard (3 min)**

1. Navigate to the org's Copilot usage dashboard
2. Show key metrics: acceptance rate, active users, languages, editors
3. Show seat management: who has a license, who's active, utilization
4. Mention: "This data is available via API — export to Excel or feed into your MSFT reporting stack."

> **Talking point:** "You're investing in Copilot. This dashboard shows you the ROI — how much code is AI-assisted, which teams are adopting, and where to focus enablement."

**Security Overview (3 min)**

5. Navigate to the org's Security Overview
6. Show the risk posture: open alerts by severity across repos
7. Show trends: alerts opened vs. closed over time, MTTR
8. Show coverage: which repos have code scanning, secret scanning, Dependabot enabled
9. Click into a repo to show the security tab drill-down

> **Talking point:** "Single pane of glass for your security team. SOC 2 auditors? Point them here. PCI compliance evidence? Export these reports."

**Audit Log (1 min)**

10. Briefly show the audit log: Copilot actions, agent actions, security events
11. Mention streaming: "You can stream these logs to Splunk, Datadog, or your SIEM."

### Transition

> "Finally, let's talk about how you keep all of this under control — governance and guardrails."

---

## Segment 8 — Governance & Guardrails (3 min)

### Goal
Reassure RCCL leadership that AI adoption doesn't mean loss of control.

### Talking Points

> "The number one question I get from leadership: 'How do we make sure AI doesn't go off the rails?' Here's the answer."

### Demo Steps

1. Show a quick summary slide of governance controls:

| Guardrail | What it does |
|---|---|
| **Rulesets** | Required reviews, status checks, branch protection |
| **Custom Instructions** | AI follows your team's standards |
| **Content Exclusion** | Block sensitive repos/files from Copilot |
| **MCP Governance** | Admin controls which MCP servers are allowed |
| **Audit Log** | Every action tracked and exportable |

2. Show one example: Copilot content exclusion settings — "This repo contains PCI data, so we exclude it from Copilot suggestions."
3. Show rulesets: "This branch requires 2 approvals, passing CI, and no unresolved code scanning alerts."

> **Talking point:** "Developers stay fast. Leadership stays informed. Security stays enforced. That's the balance GitHub is built for."

---

## Wrap-Up & Transition to Q&A

### Closing Summary (1 min)

> "Let me recap what we covered across your SDLC:
>
> - **Planning:** Jira integrates seamlessly — no workflow change required
> - **Build:** Coding Agent and Custom Instructions make Copilot work your way
> - **Test:** Playwright MCP lets Copilot drive QA automation
> - **Secure:** GHAS Autofix and Push Protection add AI-powered security on top of Snyk
> - **Deliver:** CI/CD runs automatically, dashboards show the full picture
> - **Govern:** Guardrails give leadership confidence in AI adoption
>
> The common thread: **Agentic SDLC is an evolution, not a migration.** You layer these capabilities on your existing tools and workflows."

### Transition to Q&A (20 min)

> "I'd love to hear what resonated and what questions you have. We can also dive deeper into any specific area."

**Likely Questions & Prepared Answers:**

| Question | Key Points |
|---|---|
| "How does GHAS compare to Snyk?" | Complementary — Autofix is unique to GitHub, Push Protection is pre-commit. Snyk has broader language support in some areas. Run both in parallel during an eval. |
| "Can the Coding Agent access our Jira?" | Yes, via MCP integration. The agent reads issue context from linked sources. |
| "What about IP / code privacy with Copilot?" | Enterprise-grade: no code used for training, data encryption in transit/at rest, content exclusions available. |
| "How do we measure ROI?" | Copilot Dashboard metrics + Accenture/McKinsey productivity studies. Typical: 30–55% faster task completion. |
| "What does licensing look like?" | Copilot Enterprise includes all extensibility features. GHAS can be purchased as Code Security + Secret Protection separately. |

### Transition to Workshop Draft Review (5 min)

> "Before we wrap up, I want to share a draft of a hands-on enablement workshop we can run with your development teams. Let me walk you through the outline…"

- Share the workshop draft outline
- Gather initial feedback on scope, timing, and team selection
- Propose next steps: pilot team selection, workshop scheduling, GHAS eval

---

## Post-Session Follow-Up

- [ ] Send slide deck and demo recording to attendees
- [ ] Share relevant links: docs, blog posts, GitHub roadmap
- [ ] Schedule hands-on enablement workshop
- [ ] Set up GHAS trial in a sandbox repo for parallel eval with Snyk
- [ ] Check in at 30 days post-session for feedback
- [ ] Update [panam issue](https://github.com/github/panam/issues/179#issuecomment-3993513371) with session outcomes
