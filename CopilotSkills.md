# GITHUB COPILOT SKILLS - 20 MINUTE DEMO SESSION

## TIMING BREAKDOWN

- Introduction (2 mins)
- Core Concepts (3 mins)
- Live Demo - Basic Skills (5 mins)
- Live Demo - Advanced Skills (7 mins)
- Best Practices & Q&A (3 mins)

---

## TALK TRACK

### INTRODUCTION (2 MINS)

**Opening Statement:**
"Today we're going to explore GitHub Copilot Skills - a powerful way to have natural conversations with AI about your codebase. Think of it as moving from autocomplete to having an expert pair programmer who can understand your entire repository context."

**Key Points to Hit:**
- Skills extend Copilot beyond code completion into intelligent assistance
- Works in VS Code, Visual Studio, GitHub.com, and CLI
- Uses your repo structure, files, and context automatically
- Available to all Copilot Individual, Business, and Enterprise users

---

### CORE CONCEPTS (3 MINS)

**What Are Copilot Skills?**

"Copilot Skills are specialized capabilities that let you interact with different aspects of your development workflow through natural language."

**Built-in Skills Include:**
- **@workspace** - Understands your entire codebase, file structure, and context
- **@terminal** - Helps with CLI commands, shell scripts, and debugging terminal errors
- **@vscode** - Assists with VS Code settings, extensions, and editor configuration
- **@github** - Searches repos, issues, PRs, discussions, and documentation
- **Extension Skills** - Connect to Jira, Sentry, Azure, and more

**The @ Symbol Pattern:**
"When you type @ in Copilot Chat, you're invoking a skill. Think of it as telling Copilot where to focus its attention."

---

### LIVE DEMO - BASIC SKILLS (5 MINS)

**Demo Flow:**

#### 1. SHOW @WORKSPACE IN ACTION (2 mins)

Open Copilot Chat in VS Code
Type: `@workspace what does this codebase do?`

**Talk Track:**
"Notice I didn't specify files. @workspace scans your repo structure, reads relevant files, and gives you a summary. This is incredible for onboarding new developers."

**Follow-up Query:**
`@workspace where is authentication handled?`

**Talk Track:**
"It's searching across multiple files, understanding relationships, and pointing me to specific locations. This saves hours of grep-ing through code."

#### 2. SHOW @TERMINAL SKILL (1.5 mins)

- Intentionally run a failing command or show an error in terminal
- Highlight the error, open Copilot Chat
- Click "Explain" or ask: `@terminal why did this fail?`

**Talk Track:**
"@terminal understands your shell environment, command history, and error messages. It's like having a DevOps expert on call."

#### 3. SHOW CODE CONTEXT WITHOUT @ (1.5 mins)

- Highlight a function in your editor
- Ask in Chat: `explain this function and suggest improvements`

**Talk Track:**
"Even without @, Copilot sees your highlighted code. But watch what happens when I need broader context..."

Then ask: `@workspace how is this function used across the codebase?`

**Talk Track:**
"Now it's searching everywhere this function is called. That's the power of skills - contextual awareness."

---

### LIVE DEMO - ADVANCED SKILLS (7 MINS)

**Demo Flow:**

#### 4. MULTI-FILE EDITING WITH @WORKSPACE (3 mins)

Ask: `@workspace add error handling to all API calls in the services folder`

**Talk Track:**
"This is where it gets powerful. I'm asking Copilot to understand a pattern across multiple files and apply consistent changes. In the past, this would require regex find-replace or manual updates."

- Show the suggested changes
- Accept or refine them

**Talk Track:**
"Notice it's showing me exactly what will change in each file. I maintain control but save massive amounts of time."

#### 5. SLASH COMMANDS WITHIN SKILLS (2 mins)

Show: `@workspace /tests generate unit tests for the UserService class`

**Talk Track:**
"Slash commands are shortcuts for common tasks. /tests, /fix, /doc, /explain - they work with skills to be more specific."

**Other examples to mention:**
- `@workspace /doc add JSDoc comments to all public methods`
- `@workspace /fix the bug in the checkout flow`

#### 6. AGENT MODE (2 mins)

- Open Copilot Edits (multi-file editing mode)
- Add files to the working set
- Ask: `refactor these components to use TypeScript interfaces instead of types`

**Talk Track:**
"Agent mode - or Copilot Edits - lets you work across multiple files simultaneously. Add files to your working set, describe what you want, and Copilot proposes changes across all of them. This is perfect for large refactoring tasks."

Show accept/reject flow

---

### BEST PRACTICES & TIPS (3 MINS)

**Best Practices for Your Team:**

**BE SPECIFIC WITH CONTEXT**
- Use @workspace when you need codebase-wide understanding
- Highlight code when asking about specific functions
- Reference file names: "in src/auth/login.js, how should I..."

**ITERATE YOUR PROMPTS**
- Start broad: `@workspace how does user authentication work?`
- Then narrow: `show me the JWT validation logic`
- Then act: `add refresh token support to this flow`

**USE CHAT HISTORY**
- Copilot remembers your conversation thread
- Build on previous responses
- Say "apply that pattern to the payment service too"

**LEVERAGE FOR ONBOARDING**
- `@workspace explain the folder structure`
- `@workspace what coding standards does this project use?`
- `@workspace how do I run tests?`

**VERIFY AND REVIEW**
- Always review suggestions before accepting
- Copilot is a pair programmer, not a replacement for your expertise
- Use it to accelerate, not to blindly generate

---

### COMMON DEVELOPER WORKFLOWS

**Quick examples to share:**

- **Debugging:** "I'm getting error X in the console, help me trace where it's coming from"
- **Testing:** `@workspace /tests create integration tests for the checkout flow`
- **Documentation:** `@workspace /doc create a README for the new API module`
- **Refactoring:** `@workspace identify duplicate code in the utils folder`
- **Learning:** `@workspace explain why we're using Redis here instead of in-memory cache`

---

### CLOSING STATEMENT

"The key mindset shift is this: stop thinking of Copilot as autocomplete. Think of it as an AI teammate who can read your entire codebase, understand context, and help you ship faster. The @ skills are how you tell it where to focus."

"Start simple - use @workspace to explore your code. Then gradually incorporate it into your daily workflow. The developers who get the most value are the ones who treat it as a conversation, not a one-shot command tool."

---

## RECOMMENDED DEMO REPOSITORY

If you need a good demo repo, I suggest:
- Use a microservices or full-stack app (shows cross-file context)
- Something with authentication, API routes, and database models
- TypeScript/JavaScript for broad audience familiarity

---

## Q&A PREP

**Expected Questions:**

**Q: "Does it work with our private repos?"**
A: Yes, Copilot Business/Enterprise works with all your private repositories. Content exclusions available for sensitive repos.

**Q: "What about code quality and security?"**
A: Copilot suggests code, but your review process still applies. Use code scanning and secret scanning. Enterprise includes IP indemnity.

**Q: "Can it access our databases or prod systems?"**
A: No, Copilot only sees your code files and Git history. It doesn't connect to live systems.

**Q: "How much does it cost?"**
A: $10/user/month (Business), $19/user/month (Enterprise with additional features).

---

## ADDITIONAL RESOURCES

- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)
- [Copilot Chat Skills Reference](https://docs.github.com/en/copilot/using-github-copilot/asking-github-copilot-questions-in-your-ide)
- [Best Practices Guide](https://docs.github.com/en/copilot/using-github-copilot/best-practices-for-using-github-copilot)