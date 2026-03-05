# GitHub Copilot: Instructions, Agents, Skills, Spaces & MCP

> A Solutions Engineer's guide to Copilot extensibility — what each feature does, when to recommend it, and how they work together.

## Quick Navigation

| Document | Description |
|----------|-------------|
| [Feature Breakdown](feature-breakdown.md) | Detailed explanation of each feature with use cases |
| [Comparison & Decision Guide](comparison-and-decision-guide.md) | Side-by-side table and decision tree for recommending the right feature |
| [Slide Deck (Marp)](slide-deck.md) | Customer-facing presentation (render with [Marp](https://marp.app)) |

## TL;DR

| Feature | One-Liner |
|---------|-----------|
| **Copilot Instructions** | Always-on coding rules and standards baked into every suggestion |
| **Copilot Agents** | Autonomous AI teammates that complete tasks end-to-end (coding agent, custom agents) |
| **Copilot Skills** | Reusable, portable playbooks that teach Copilot how to perform specific tasks |
| **Copilot Spaces** | Shared, persistent knowledge hubs that ground Copilot in curated project context |
| **MCP** | Universal protocol for connecting Copilot to external tools, APIs, and data sources |

## How They Complement Each Other

```
┌──────────────────────────────────────────────────────────┐
│                    Copilot Spaces                        │
│         (shared context & knowledge layer)               │
│                                                          │
│  ┌────────────────┐  ┌──────────────────────────────┐    │
│  │  Instructions  │  │         MCP Servers           │    │
│  │ (always-on     │  │  (external tools & data)      │    │
│  │  standards)    │  │                               │    │
│  └───────┬────────┘  └──────────────┬───────────────┘    │
│          │                          │                    │
│          ▼                          ▼                    │
│  ┌──────────────────────────────────────────────────┐    │
│  │              Copilot Agents                       │    │
│  │  (autonomous task execution with personas)        │    │
│  │                                                   │    │
│  │    ┌──────────────────────────────────────┐       │    │
│  │    │          Copilot Skills              │       │    │
│  │    │  (reusable procedures agents load)   │       │    │
│  │    └──────────────────────────────────────┘       │    │
│  └──────────────────────────────────────────────────┘    │
└──────────────────────────────────────────────────────────┘
```

**Instructions** set the rules. **Skills** provide reusable know-how. **Agents** execute autonomously using both. **Spaces** supply shared context. **MCP** connects it all to external systems.
