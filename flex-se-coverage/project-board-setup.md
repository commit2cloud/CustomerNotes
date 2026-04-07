# GitHub Project Board Setup Guide — Flex SE Coverage Tracking

This guide walks through setting up a GitHub Project (v2) board to track and manage Flex SE coverage requests.

## Step 1: Create the Project

1. Go to the **organization** or **user profile** → **Projects** tab
2. Click **New project**
3. Choose **Board** layout (can add Table view later)
4. Name it: **Flex SE Coverage Requests**
5. Set visibility as appropriate (Private for internal use)

## Step 2: Configure Columns (Status Field)

Set up the following status columns to track request lifecycle:

| Column | Purpose |
|---|---|
| **📥 New Requests** | Incoming requests awaiting review |
| **🔍 Under Review** | @nathos is evaluating the request |
| **✅ Approved & Assigned** | Flex SE has been assigned |
| **🔄 Active Coverage** | Flex SE is currently covering |
| **📋 Handoff / Debrief** | SE returning, handoff in progress |
| **✔️ Completed** | Coverage period ended, debrief done |
| **❌ Declined** | Request was declined (with reason) |

## Step 3: Add Custom Fields

Add these custom fields to the Project for richer filtering and sorting:

| Field Name | Type | Purpose |
|---|---|---|
| **Priority** | Single select (`Critical`, `High`, `Standard`) | Prioritize requests |
| **Coverage Start** | Date | When coverage begins |
| **Coverage End** | Date | When coverage ends |
| **Assigned Flex SE** | Single select or Text | Which Flex SE is covering |
| **Region** | Single select (e.g., `Americas`, `EMEA`, `APAC`) | Filter by geography |
| **Requesting Manager** | Text | Who submitted the request |

### How to Add Custom Fields
1. Open the Project
2. Click **+** next to the field headers (in Table view) or use **Settings** → **Fields**
3. Click **New field**
4. Choose field type and add options as listed above

## Step 4: Create Saved Views

Set up multiple views for different perspectives:

### View 1: "Manager Dashboard" (Default Board)
- **Layout:** Board
- **Group by:** Status
- **Sort by:** Priority (Critical first)
- **Filter:** `status:not("Completed", "Declined")`

### View 2: "Active Coverage" (Table)
- **Layout:** Table
- **Filter:** `status:"Active Coverage"`
- **Columns:** Title, Assigned Flex SE, Coverage Start, Coverage End, Priority

### View 3: "Upcoming Coverage" (Table)
- **Layout:** Table
- **Filter:** `status:"Approved & Assigned"`
- **Sort by:** Coverage Start (ascending)
- **Columns:** Title, Coverage Start, Coverage End, Assigned Flex SE, Requesting Manager

### View 4: "All Requests" (Table)
- **Layout:** Table
- **Filter:** none (show all)
- **Sort by:** Created date (newest first)

## Step 5: Link the Repository

1. In the Project **Settings** → **Manage access**
2. Add the repository where the issue form template lives
3. This allows new issues to automatically appear in the Project

### Auto-Add Issues to Project
To automatically add new coverage request issues to the Project:
1. Go to Project **Settings** → **Workflows** (built-in)
2. Enable **"Auto-add to project"**
3. Set filter: `label:flex-se-coverage`
4. This ensures every new coverage request issue shows up on the board automatically

## Step 6: Create Labels in the Repository

Create these labels in the repo that houses the issue form:

| Label | Color | Description |
|---|---|---|
| `flex-se-coverage` | `#0075ca` | Flex SE coverage request |
| `pending-review` | `#e4e669` | Awaiting Flex SE Manager review |
| `approved` | `#0e8a16` | Request approved |
| `assigned` | `#1d76db` | Flex SE has been assigned |
| `active-coverage` | `#5319e7` | Coverage currently in progress |
| `completed` | `#6f6f6f` | Coverage completed |
| `declined` | `#d93f0b` | Request declined |
| `critical-priority` | `#b60205` | Critical priority request |
| `high-priority` | `#ff9f1c` | High priority request |
| `standard-priority` | `#c2e0c6` | Standard priority request |

### Quick Setup via GitHub CLI

```bash
# Run these commands in the target repository
gh label create "flex-se-coverage" --color "0075ca" --description "Flex SE coverage request"
gh label create "pending-review" --color "e4e669" --description "Awaiting Flex SE Manager review"
gh label create "approved" --color "0e8a16" --description "Request approved"
gh label create "assigned" --color "1d76db" --description "Flex SE has been assigned"
gh label create "active-coverage" --color "5319e7" --description "Coverage currently in progress"
gh label create "completed" --color "6f6f6f" --description "Coverage completed"
gh label create "declined" --color "d93f0b" --description "Request declined"
gh label create "critical-priority" --color "b60205" --description "Critical priority request"
gh label create "high-priority" --color "ff9f1c" --description "High priority request"
gh label create "standard-priority" --color "c2e0c6" --description "Standard priority request"
```

## Step 7: Notify the Team

Once everything is set up:

1. **Share the repo link** with SE Managers/Directors — they just need to click "New Issue" and select the coverage request template
2. **@nathos** should **Watch** the repository (or at minimum subscribe to the `flex-se-coverage` label) to get notifications on new requests
3. **Pin an issue** in the repo with instructions for requestors
4. **Bookmark the Project board** for quick access to the dashboard

---

## Ongoing Maintenance

| Task | Frequency | Owner |
|---|---|---|
| Review new requests on the board | Weekly (or as notified) | @nathos |
| Move cards through status columns | As status changes | @nathos / Flex SEs |
| Close completed coverage issues | When debrief is done | Assigned Flex SE |
| Review/update issue form template | Quarterly or as needed | Flex SE team |

## Tips

- **Use issue comments** for handoff notes, debrief summaries, and ongoing updates — this creates a complete record
- **Pin important issues** to keep high-priority requests visible
- **Use milestones** to group requests by quarter if volume grows
- **@mention the assigned Flex SE** in the issue when assigning them so they get notified
