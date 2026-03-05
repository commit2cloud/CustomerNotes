# GitHub Copilot Extensibility: Feature Breakdown

> What each feature is, what it does, and when to recommend it.

---

## 1. Copilot Instructions

### What It Is

Copilot Instructions are persistent, always-on rules and guidelines that shape how Copilot generates code and responses for a repository, directory, or user. They act as the "company policy" layer — every suggestion and chat response automatically respects these rules without the user needing to repeat them.

### How It Works

| Scope | File | Effect |
|-------|------|--------|
| **Repository-wide** | `.github/copilot-instructions.md` | Applied to every Copilot interaction in the repo |
| **Path-specific** | `.github/instructions/*.instructions.md` | Applied only when working with files matching a glob pattern (set via YAML frontmatter) |
| **Agent-specific** | `AGENTS.md` / `.github/agents/*.agent.md` | Instructions scoped to specific agent personas |
| **User-level** | IDE settings (VS Code, JetBrains) | Personal rules applied to all repos for that user |
| **Organization-level** | Copilot policy settings | Org-wide rules enforced across all members |

### Ideal Use Cases

- Enforce coding standards (naming conventions, formatting, test frameworks)
- Set security requirements (cookie settings, input validation, dependency rules)
- Define architecture guidelines (preferred patterns, forbidden anti-patterns)
- Standardize documentation and comment style
- Restrict Copilot behavior ("never refactor unless asked", "always use TypeScript")

### Customer Conversation Starters

> *"Do your teams struggle with inconsistent AI suggestions across developers?"*
> *"Do you have coding standards that Copilot keeps ignoring?"*
> *"Do different parts of your codebase need different rules?"*

### Key Links

- [GitHub Docs: Adding repository custom instructions](https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions)
- [VS Code Blog: Context is all you need](https://code.visualstudio.com/blogs/2025/03/26/custom-instructions)

---

## 2. Copilot Agents

### What It Is

Copilot Agents are autonomous AI entities that can execute multi-step tasks end-to-end. There are two main categories:

1. **Coding Agent** — GitHub's built-in agent that works asynchronously on issues and PRs
2. **Custom Agents** — User-defined agent personas with specific instructions and tool access

### Coding Agent

The coding agent is an autonomous software engineering agent that runs in the cloud. You assign it a task (via a GitHub Issue, PR comment, or Copilot Chat), and it independently:

1. Spins up a secure, isolated environment (via GitHub Actions)
2. Reads repo context, issues, and discussions
3. Makes code changes across multiple files
4. Runs your existing CI/CD pipeline (builds, tests, linters)
5. Opens a draft pull request for human review
6. Iterates based on PR review feedback

**Key constraints:**
- Cannot merge its own PRs — human review is always required
- Operates only on branches it creates (`copilot/*`)
- Only users with write access can assign tasks
- Every action is logged for transparency

### Custom Agents

Custom agents are specialized personas defined in `.github/agents/*.agent.md` files. Each agent can have:

- A unique name and description
- Specific instructions and behavioral rules
- Restricted tool access (only use certain MCP servers, skills, etc.)
- Defined areas of expertise

**Examples:** Security Reviewer, Documentation Writer, Frontend Specialist, Database Admin

### Ideal Use Cases

| Agent Type | Best For |
|-----------|----------|
| **Coding Agent** | Bug fixes, test coverage, documentation updates, small features, tech debt cleanup |
| **Custom Agents** | Role-based workflows, enforcing guardrails, separating concerns across team functions |

### Customer Conversation Starters

> *"Do your developers spend time on repetitive tasks like adding tests or fixing lint errors?"*
> *"Would it help to have an AI handle well-defined issues while your team focuses on architecture?"*
> *"Do you need different AI behavior for security reviews vs. feature development?"*

### Key Links

- [GitHub Docs: About the coding agent](https://docs.github.com/en/copilot/concepts/agents/coding-agent/about-coding-agent)
- [GitHub Blog: Coding agent 101](https://github.blog/ai-and-ml/github-copilot/github-copilot-coding-agent-101-getting-started-with-agentic-workflows-on-github/)

---

## 3. Copilot Skills

### What It Is

Skills are modular, reusable "playbooks" that teach Copilot how to perform specific tasks in a structured, repeatable way. Think of them as recipes — each skill focuses on one well-defined workflow and can be loaded on-demand by any agent.

### How It Works

Skills are stored as directories in your repository:

```
.github/skills/
├── playwright-testing/
│   └── SKILL.md
├── security-audit/
│   └── SKILL.md
└── api-documentation/
    └── SKILL.md
```

Each `SKILL.md` contains:
- A description of what the skill does (used for auto-matching)
- Step-by-step instructions
- Scripts, templates, or reference materials
- Examples of expected input/output

Copilot automatically detects and loads relevant skills when a user's prompt matches the skill's description, reducing context overload.

### Ideal Use Cases

- Standardize repeatable workflows (test generation, CI/CD debugging, migration steps)
- Package domain expertise into portable, shareable units
- Teach Copilot project-specific procedures (onboarding, release processes)
- Share best practices across repos and teams
- Compose complex workflows by combining multiple skills

### How Skills Differ from Instructions

| | Instructions | Skills |
|---|---|---|
| **When active** | Always on | On-demand (matched to prompt) |
| **Purpose** | Rules and standards | Procedures and workflows |
| **Analogy** | Company policy | Standard operating procedure |
| **Scope** | Broad (repo or path) | Narrow (specific task) |

### Customer Conversation Starters

> *"Do your teams have tribal knowledge that's hard to document and share?"*
> *"Do you want Copilot to follow specific step-by-step procedures for certain tasks?"*
> *"Would it be useful to package your team's best practices so any developer can use them?"*

### Key Links

- [GitHub Docs: About agent skills](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills)
- [GitHub Docs: Creating agent skills](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/create-skills)
- [VS Code Docs: Agent skills](https://code.visualstudio.com/docs/copilot/customization/agent-skills)

---

## 4. Copilot Spaces

### What It Is

Copilot Spaces are persistent, collaborative knowledge hubs that ground Copilot in curated project context. Instead of Copilot only knowing about the file you're editing, a Space aggregates code, documentation, specs, custom instructions, and notes — making Copilot a true project expert.

### How It Works

1. **Create a Space** on GitHub for a project or area of work
2. **Add context** — attach repositories, upload documents, write instructions, link issues
3. **Interact** — use Copilot Chat within the Space; responses are grounded in all attached context
4. **Collaborate** — share with your org, specific teams, or publicly
5. **Sync with IDE** — access Space context from VS Code via the GitHub MCP server

### Key Capabilities

- **Always up-to-date:** Context from attached repos updates automatically as source changes
- **Fine-grained sharing:** Private (team), org-wide, or public Spaces
- **Persistent conversations:** Chat history is saved for reference
- **Custom instructions per Space:** Tailor Copilot behavior to the Space's purpose
- **Replaces Knowledge Bases:** Copilot Knowledge Bases were deprecated Sept 2025 in favor of Spaces

### Ideal Use Cases

- Onboard new team members with shared project context
- Preserve institutional knowledge and design decisions
- Ensure consistent AI responses across a team working on the same project
- Run demos, prototypes, or workshops with pre-loaded context
- Create subject-matter-expert Spaces (e.g., "Platform Architecture", "Security Guidelines")

### Customer Conversation Starters

> *"How do you onboard new developers to your projects today?"*
> *"Do your teams lose context when people switch projects or leave?"*
> *"Would it help if every developer on a project had the same AI-powered knowledge base?"*

### Key Links

- [GitHub Changelog: Introducing Copilot Spaces](https://github.blog/changelog/2025-05-29-introducing-copilot-spaces-a-new-way-to-work-with-code-and-context/)
- [GitHub Docs: Using Copilot Spaces](https://docs.github.com/en/copilot/how-tos/provide-context/use-copilot-spaces/use-copilot-spaces)

---

## 5. MCP (Model Context Protocol)

### What It Is

MCP is an open standard that provides a universal way for AI models to communicate with external tools, APIs, and data sources. Think of it as "USB-C for AI integrations" — instead of building custom integrations for every tool, MCP provides a single, consistent protocol.

### How It Works

```
┌─────────────┐     MCP Protocol     ┌─────────────┐
│   Copilot    │ ◄──────────────────► │ MCP Server  │
│  (Client)    │    JSON-RPC over     │  (Tool/API) │
│              │    HTTP/WebSocket    │             │
└─────────────┘                      └─────────────┘
```

1. Copilot (the MCP client) discovers available tools from an MCP server
2. User prompts trigger Copilot to invoke tools or retrieve data
3. MCP server returns structured responses
4. Results are integrated into Copilot's context and responses

### Available MCP Servers

MCP servers can expose any external capability to Copilot:

| Category | Examples |
|----------|----------|
| **GitHub** | GitHub MCP Server (PRs, issues, code search, Actions) |
| **Design** | Figma MCP Server (fetch designs, generate matching code) |
| **Databases** | PostgreSQL, MongoDB, Redis MCP servers |
| **DevOps** | Docker, Kubernetes, Terraform MCP servers |
| **Documentation** | Confluence, Notion MCP servers |
| **Custom** | Your own internal tools and APIs |

### Enterprise Governance

Organizations can control MCP server access through Copilot policy settings:
- Approve/deny specific MCP servers
- Set authentication requirements (OAuth, PAT)
- Audit tool usage across the organization

### Ideal Use Cases

- Connect Copilot to internal APIs, databases, or proprietary tools
- Bridge design and development workflows (e.g., Figma → code)
- Enable Copilot to manage GitHub resources (issues, PRs, Actions)
- Automate DevOps tasks from within the IDE
- Standardize AI-tool integration across the organization

### Customer Conversation Starters

> *"Does your team switch between many tools during development?"*
> *"Do you have internal APIs or tools that would be useful for Copilot to access?"*
> *"Are you concerned about governing which external tools your AI assistants can use?"*

### Key Links

- [GitHub Docs: About MCP](https://docs.github.com/en/copilot/concepts/context/mcp)
- [GitHub Blog: 5 ways to transform your workflow with MCP](https://github.blog/ai-and-ml/github-copilot/5-ways-to-transform-your-workflow-using-github-copilot-and-mcp/)
