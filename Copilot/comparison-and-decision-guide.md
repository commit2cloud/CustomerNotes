# Comparison & Decision Guide

> Side-by-side comparison table and decision tree for recommending the right GitHub Copilot extensibility feature.

---

## Feature Comparison Table

| Dimension | Instructions | Agents | Skills | Spaces | MCP |
|-----------|-------------|--------|--------|--------|-----|
| **What it is** | Always-on rules for Copilot | Autonomous AI entities that execute tasks | Reusable task playbooks | Persistent shared knowledge hubs | Protocol for external tool integration |
| **Analogy** | Company policy | Junior developer on your team | Standard operating procedures | Team wiki + AI expert | Universal power adapter |
| **When active** | Every interaction | On assignment or invocation | On-demand (auto-matched to prompt) | When Space is open/attached | When MCP server is configured |
| **Where it lives** | `.github/copilot-instructions.md`, `.instructions.md` files | GitHub Issues/PRs (coding agent), `.github/agents/` (custom) | `.github/skills/*/SKILL.md` | GitHub.com (Spaces UI) | IDE settings / `.vscode/mcp.json` |
| **Who creates it** | Developers / team leads | GitHub (coding agent) / developers (custom agents) | Developers / team leads | Any team member | Tool providers / platform teams |
| **Scope** | Repo, path, user, or org | Task-level (coding agent) or session-level (custom) | Task-level | Project or topic-level | Tool/service-level |
| **Requires code?** | No (markdown only) | No (assign issues) / Yes (custom agent definitions) | No (markdown + optional scripts) | No | Yes (server implementation or config) |
| **Shareable?** | Via repo (committed to source) | Custom agents via repo | Via repo, cross-platform compatible | Org, team, or public sharing | MCP servers are reusable across projects |
| **Plan required** | Copilot Individual+ | Copilot Enterprise / Business | Copilot Individual+ | Copilot Enterprise / Business | Copilot Individual+ |

---

## Decision Tree

Use this flowchart to recommend the right feature based on the customer's need.

```
START: What does the customer want to do?
│
├─► "Enforce coding standards and rules across our team"
│   └─► ✅ Copilot Instructions
│       • Use .github/copilot-instructions.md for repo-wide rules
│       • Use .instructions.md files for path-specific rules
│
├─► "Have AI autonomously complete tasks (fix bugs, write tests, etc.)"
│   └─► ✅ Coding Agent
│       • Assign GitHub Issues to @copilot
│       • Agent works in background, opens draft PR
│
├─► "Define specialized AI personas for different workflows"
│   └─► ✅ Custom Agents
│       • Create .agent.md files in .github/agents/
│       • Each agent has its own instructions and tool access
│
├─► "Package and share repeatable procedures"
│   └─► ✅ Skills
│       • Create SKILL.md files in .github/skills/
│       • Auto-loaded when prompts match the skill description
│
├─► "Give Copilot deep knowledge about our project/domain"
│   └─► ✅ Spaces
│       • Create a Space, attach repos, docs, and instructions
│       • Share with team for consistent project context
│
├─► "Connect Copilot to external tools, APIs, or data sources"
│   └─► ✅ MCP
│       • Configure MCP servers in IDE settings
│       • Copilot can invoke tools and retrieve data
│
└─► "All of the above / complex workflow"
    └─► 🔀 Combine them:
        • Instructions = rules
        • Skills = procedures
        • Agents = execution
        • Spaces = shared context
        • MCP = external connections
```

---

## Common Customer Scenarios

### Scenario 1: "We want consistent code quality across 50 developers"

**Recommend:** Copilot Instructions + Spaces

- **Instructions** enforce coding standards, naming conventions, and security requirements in every suggestion
- **Spaces** share project-specific context so every developer gets the same caliber of AI assistance
- Combine with org-level Copilot policy settings for governance

### Scenario 2: "Our developers waste time on boilerplate tasks"

**Recommend:** Coding Agent + Skills

- **Coding Agent** handles well-defined tasks autonomously (test coverage, doc updates, dependency bumps)
- **Skills** standardize how those tasks are performed, ensuring consistency
- Developers review draft PRs instead of doing the work themselves

### Scenario 3: "We need Copilot to work with our internal tools"

**Recommend:** MCP

- Build or configure **MCP servers** for internal APIs, databases, or proprietary tools
- Copilot can query data, trigger actions, and integrate results — all from the IDE
- Enterprise governance controls which servers are approved

### Scenario 4: "Different teams need different AI behavior"

**Recommend:** Custom Agents + Instructions

- **Custom Agents** provide role-based personas (Security Reviewer, Frontend Dev, DevOps Engineer)
- **Instructions** set baseline rules that apply across all agents
- Each agent can have its own tool restrictions and behavioral guidelines

### Scenario 5: "We're onboarding new developers and they need to ramp up fast"

**Recommend:** Spaces + Instructions + Skills

- **Spaces** aggregate project documentation, architecture decisions, and key context
- **Instructions** ensure AI suggestions match team conventions from day one
- **Skills** package onboarding procedures into structured, repeatable playbooks

### Scenario 6: "We want to automate our security review process"

**Recommend:** Custom Agent + Skills + MCP

- **Custom Agent** persona: "Security Reviewer" with restricted tools and strict instructions
- **Skills** define security audit procedures (OWASP checklist, dependency scanning steps)
- **MCP** connects to security scanning tools (Snyk, Dependabot, internal SAST)

---

## How They Layer Together

| Layer | Feature | Purpose |
|-------|---------|---------|
| **Foundation** | Instructions | Set the rules every interaction must follow |
| **Knowledge** | Spaces | Provide shared, persistent project context |
| **Connectivity** | MCP | Bridge to external tools and data sources |
| **Expertise** | Skills | Package reusable know-how for specific tasks |
| **Execution** | Agents | Autonomously execute work using all of the above |

> **Key insight:** These features are not competing alternatives — they are complementary layers. The most effective setups combine multiple features.

---

## Quick Qualification Questions

Use these questions to quickly identify which feature(s) to recommend:

| Question | If "Yes", Recommend |
|----------|-------------------|
| Do you need AI to follow specific coding rules automatically? | **Instructions** |
| Do you want AI to complete tasks without developer involvement? | **Coding Agent** |
| Do you need different AI behavior for different roles/workflows? | **Custom Agents** |
| Do you have repeatable procedures you want AI to follow? | **Skills** |
| Do you need to share project knowledge across a team? | **Spaces** |
| Do you need Copilot to interact with external tools or APIs? | **MCP** |
| Do you need enterprise governance over AI capabilities? | **MCP + Org Policies** |
