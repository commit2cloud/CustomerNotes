# Flex SE Coverage Request Mechanism — Planning Document

## Problem Statement

Flex SEs cover for Solution Engineers going on extended leave (typically >1 month). SE Managers/Directors need a way to submit coverage requests so the Flex SE Manager (@nathos) can review, prioritize, and assign them.

**Key information needed per request:**
- SE who needs coverage (name/handle)
- Account Executive(s) the SE covers
- Dates of coverage needed (start and end)
- Relevant account context (strategic accounts, ongoing opportunities, busy patches)
- Coverage plans if no Flex SE is available (fallback/contingency)

**Requirements:**
- Easy for Managers/Directors to submit
- Guided experience (users know what info to provide)
- Manager (@nathos) can review all requests in one place and assign
- MVP within the standard GitHub/Microsoft stack
- **High maintainability** — must not break easily

---

## Options Analysis

### Option 1: GitHub Issue Forms + Project Board ⭐ RECOMMENDED MVP

**How it works:**
- Create a [GitHub Issue Form](https://docs.github.com/en/communities/using-templates/syntax-for-githubs-form-schema) (YAML-based template) in a dedicated repo (e.g., `flex-se-requests`)
- Each new issue = one coverage request, with structured fields pre-defined
- Use a [GitHub Project (v2)](https://docs.github.com/en/issues/planning-and-tracking-with-projects) board for @nathos to view, filter, sort, and assign requests
- Use labels for status tracking (`pending-review`, `approved`, `assigned`, `completed`, `declined`)

**What gets built:**
1. Issue form template (`.github/ISSUE_TEMPLATE/flex-se-coverage-request.yml`) — included in this PR
2. GitHub Project board with custom fields (Priority, Coverage Dates, Assigned Flex SE)
3. Labels for workflow status

**Pros:**
- ✅ **Zero code to maintain** — pure GitHub-native configuration (YAML + Project board)
- ✅ **Guided UX** — issue forms enforce structure with dropdowns, date fields, required sections
- ✅ **Built-in notifications** — assignees and subscribers get notified automatically
- ✅ **Full audit trail** — comments, edits, timeline all tracked per issue
- ✅ **Searchable/filterable** — Project board views with custom filters (by date, priority, status)
- ✅ **No external dependencies** — lives entirely in GitHub
- ✅ **Familiar to SEs** — everyone already uses GitHub Issues daily
- ✅ **Free** — no additional cost

**Cons:**
- ❌ Date fields in issue forms are text (no native date picker in issue forms), though Project board custom fields support dates
- ❌ No automatic calendar/scheduling view (would need manual triage)
- ❌ Requestors need a GitHub account (not an issue for internal SE Managers)

**Level of Effort:** 🟢 **Low** (1-2 hours)
- Issue form template: 30 min
- Project board setup + custom fields: 30 min
- Labels + documentation: 30 min

**Maintainability:** 🟢 **Excellent** — YAML config, nothing to break. GitHub maintains the platform.

---

### Option 2: GitHub Issue Ops (Issue Forms + GitHub Actions Automation)

**How it works:**
- Same Issue Form as Option 1, **plus** GitHub Actions workflows that automate:
  - Auto-labeling based on form content (e.g., "strategic-account" label)
  - Auto-assignment to @nathos on creation
  - Slack/Teams notifications when a new request is filed
  - Automated reminders for upcoming coverage dates
  - Auto-close issues when coverage end date passes

**What gets built:**
1. Everything from Option 1
2. GitHub Actions workflows (`.github/workflows/`) for automation
3. Optional: Slack/Teams webhook integration

**Pros:**
- ✅ All benefits of Option 1
- ✅ **Reduced manual work** — auto-labeling, auto-assignment, reminders
- ✅ **Proactive notifications** — Slack/Teams alerts keep coverage top-of-mind
- ✅ **Lifecycle automation** — issues auto-close when coverage ends

**Cons:**
- ❌ **More to maintain** — workflow YAML can break on GitHub Actions runner updates or API changes
- ❌ Requires Actions minutes (free tier is usually sufficient)
- ❌ Slack/Teams webhook setup adds configuration
- ❌ Over-engineering risk for a small team

**Level of Effort:** 🟡 **Medium** (4-8 hours)
- Everything from Option 1: 1-2 hours
- Auto-label workflow: 1-2 hours
- Notification workflow: 1-2 hours
- Reminder/auto-close workflow: 1-2 hours

**Maintainability:** 🟡 **Moderate** — workflows need occasional updates if Actions syntax or APIs change.

---

### Option 3: Microsoft Forms + Excel/SharePoint List

**How it works:**
- Create a Microsoft Form with all required fields
- Responses automatically populate a SharePoint List or Excel workbook (via Power Automate)
- @nathos reviews the spreadsheet/list and updates status columns
- Optional: Power Automate flow sends email/Teams notification on new submissions

**What gets built:**
1. Microsoft Form with structured questions
2. SharePoint List or Excel workbook (auto-populated)
3. Optional: Power Automate flow for notifications

**Pros:**
- ✅ **Very familiar** — anyone can fill out a form, anyone can read a spreadsheet
- ✅ **Rich form fields** — native date pickers, dropdowns, conditional logic
- ✅ **No GitHub knowledge required** for requestors
- ✅ **Excel views** — sort, filter, pivot as needed
- ✅ **Calendar integration** possible via Outlook/Teams

**Cons:**
- ❌ **Lives outside GitHub** — context-switching between tools
- ❌ **No audit trail of discussions** — comments/follow-ups happen separately (email, Teams)
- ❌ **Data scattered** — request data in SharePoint, account context in GitHub, discussions in Teams
- ❌ **Power Automate maintenance** — flows can break silently
- ❌ **No version control** — harder to track changes to the process itself
- ❌ Doesn't showcase GitHub capabilities (we're GitHub SEs!)

**Level of Effort:** 🟡 **Medium** (3-5 hours)
- Microsoft Form creation: 1 hour
- SharePoint List / Excel setup: 1-2 hours
- Power Automate flow: 1-2 hours

**Maintainability:** 🟡 **Moderate** — Power Automate flows can break; Excel sheets can get messy over time.

---

### Option 4: GitHub Discussions (Structured Categories)

**How it works:**
- Create a Discussion category "Flex SE Coverage Requests" in a dedicated repo
- Use a Discussion template (category form) to guide requestors
- @nathos reviews discussions, converts approved ones to Issues for tracking
- Or just use Discussions as the full lifecycle

**Pros:**
- ✅ **Conversational** — threaded replies make it easy to ask clarifying questions
- ✅ **Lower barrier** — feels less formal than filing an issue
- ✅ **Upvoting** — team can signal priority via reactions
- ✅ **Category forms** — structured input similar to issue forms

**Cons:**
- ❌ **No Project board integration** — Discussions can't be added to Projects (Issues can)
- ❌ **No labels/assignees on Discussions** — harder to track status
- ❌ **Conversion friction** — converting Discussion → Issue is manual
- ❌ **Less structured workflow** — no clear lifecycle management

**Level of Effort:** 🟢 **Low** (1-2 hours)
- Discussion category + form: 30 min
- Documentation: 30 min

**Maintainability:** 🟢 **Excellent** — simple config, but limited workflow capabilities.

---

### Option 5: Agentic Workflow (Copilot-Powered)

**How it works:**
- Build a Copilot Extension or use Copilot Coding Agent to process natural language coverage requests
- Requestor opens an issue or sends a Slack message; an agent parses it, validates completeness, and creates a structured tracking issue
- Agent could also suggest Flex SE assignments based on availability and account overlap

**Pros:**
- ✅ **Cutting-edge** — showcases GitHub Copilot capabilities (great for SE storytelling)
- ✅ **Natural language input** — requestors just describe what they need
- ✅ **Smart suggestions** — agent could recommend Flex SE based on workload

**Cons:**
- ❌ **Significant build effort** — custom Copilot Extension development
- ❌ **Highest maintenance** — dependent on Copilot APIs, which are evolving rapidly
- ❌ **Overkill for current scale** — team is small enough that a form suffices
- ❌ **Debugging complexity** — when it breaks, it's harder to fix than YAML

**Level of Effort:** 🔴 **High** (20-40+ hours)
- Copilot Extension scaffolding: 4-8 hours
- NLP parsing + validation logic: 8-16 hours
- Integration + testing: 8-16 hours

**Maintainability:** 🔴 **Low** — dependent on rapidly evolving APIs; requires active development.

---

## Recommendation

### Start with Option 1 (Issue Forms + Project Board) as the MVP

**Why:**
1. **Lowest effort, highest value** — 1-2 hours to set up, zero ongoing maintenance
2. **Fully meets all requirements** — structured input, manager review, assignment, status tracking
3. **Dog-fooding GitHub** — as SEs, we should use our own tools
4. **Easy to extend later** — add Actions automation (Option 2) incrementally when/if needed
5. **Nothing to break** — pure configuration, no code

### Suggested Evolution Path

```
Phase 1 (Now):     Issue Form + Project Board           → MVP, ~2 hours
Phase 2 (If needed): Add GitHub Actions automation       → +4-6 hours
Phase 3 (Optional):  Agentic enhancement for fun/demos   → +20 hours
```

---

## MVP Implementation Included in This PR

| Deliverable | Path | Description |
|---|---|---|
| Issue Form Template | `.github/ISSUE_TEMPLATE/flex-se-coverage-request.yml` | Ready-to-use structured form for coverage requests |
| Project Board Setup Guide | `flex-se-coverage/project-board-setup.md` | Step-by-step instructions for setting up the GitHub Project |
| This Planning Doc | `flex-se-coverage/README.md` | Full options analysis (you're reading it) |

### Next Steps After Merge

1. **Create a dedicated repo** (e.g., `flex-se-requests`) or use an existing team repo
2. Copy the issue form template to that repo's `.github/ISSUE_TEMPLATE/`
3. Follow the Project Board Setup Guide to create the tracking board
4. Share the repo link with SE Managers/Directors
5. @nathos subscribes to the repo for notifications
