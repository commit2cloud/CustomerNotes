# GITHUB COPILOT SKILLS - 20 MINUTE DEMO SESSION

## TIMING BREAKDOWN

- Introduction (2 mins)
- What Are Custom Skills (3 mins)
- Pre-Built Skills Demo (6 mins)
- Live Skill Creation (6 mins)
- Best Practices & Q&A (3 mins)

---

## TALK TRACK

### INTRODUCTION (2 MINS)

**Opening Statement:**

"Today we're diving into GitHub Copilot Skills - specifically, how you can create custom skills to extend Copilot with your team's unique workflows, tools, and domain knowledge. Think of skills as teaching Copilot new capabilities that are specific to your organization."

**Key Points to Hit:**

- Skills are declarative YAML definitions stored in `.github/skills.yml`
- They extend Copilot Chat with custom `@skillname` commands
- Two types: **prompt-based** (instructions) and **URL-based** (API integrations)
- Work across VS Code, Visual Studio, GitHub.com, and CLI
- Available in Copilot Business and Enterprise

**The Value Proposition:**

"Out of the box, Copilot knows general programming. But it doesn't know YOUR deployment process, YOUR coding standards, YOUR internal APIs. Custom skills bridge that gap."

---

### WHAT ARE CUSTOM SKILLS (3 MINS)

**Core Concept:**

"Custom Copilot Skills are defined in a `.github/skills.yml` file in your repository. When developers type `@skillname` in Copilot Chat, they're invoking that custom capability."

**TWO TYPES OF SKILLS**

**1. PROMPT-BASED SKILLS**

"These transform the user's query with additional instructions or context before sending it to Copilot."

Example use cases:
- Enforce coding standards ("always use our error handling pattern")
- Provide domain context ("explain this in terms of our e-commerce platform")
- Guide responses ("format output as a security report")

**2. URL-BASED SKILLS**

"These call external APIs or webhooks, bringing external data into the Copilot conversation."

Example use cases:
- Query internal documentation systems
- Check deployment status from CI/CD
- Look up ticket details from Jira/ServiceNow
- Fetch API schemas from internal catalogs

**File Structure:**

```yaml
skills:
  - name: skillname
    description: "What this skill does"
    type: prompt | url
    prompt: "Instructions for Copilot" # for prompt-based
    url: "https://api.example.com/endpoint" # for URL-based
```

---

### PRE-BUILT SKILLS DEMO (6 MINS)

**Setup:**
Have a demo repo with `.github/skills.yml` already configured with 2-3 skills ready to showcase.

---

#### EXAMPLE 1: PROMPT-BASED SKILL - CODE STANDARDS (2 mins)

**Skill Definition:**

```yaml
skills:
  - name: standards
    description: "Review code against our team coding standards"
    type: prompt
    prompt: |
      You are a code reviewer enforcing our team standards:
      - All functions must have JSDoc comments
      - Use async/await, never callbacks
      - Error handling must use our custom ErrorHandler class
      - All API calls must include timeout configuration
      
      Review the code and provide specific feedback on violations.
```

**Demo Flow:**

1. Highlight a function in VS Code that violates standards
2. In Copilot Chat, type: `@standards review this function`
3. Show Copilot's response with specific standard violations

**Talk Track:**

"Notice I created a custom reviewer that knows our team's specific rules. I didn't have to repeat our standards - the skill carries that context automatically. This is perfect for onboarding new developers who are learning your patterns."

---

#### EXAMPLE 2: PROMPT-BASED SKILL - DOCUMENTATION FORMATTER (2 mins)

**Skill Definition:**

```yaml
skills:
  - name: docs
    description: "Generate documentation in our team's standard format"
    type: prompt
    prompt: |
      Generate documentation using our standard template:
      
      ## Overview
      Brief description (2-3 sentences)
      
      ## Usage
      Code example with imports
      
      ## Parameters
      Table with: Name | Type | Required | Description
      
      ## Returns
      Description of return value
      
      ## Example
      Real-world usage scenario
      
      Use Markdown. Be concise.
```

**Demo Flow:**

1. Highlight a function
2. Type: `@docs document this function`
3. Show formatted output matching your template

**Talk Track:**

"Every team has their own documentation style. Instead of manually formatting every time, we encode it once as a skill. Now everyone generates consistent docs automatically."

---

#### EXAMPLE 3: URL-BASED SKILL - INTERNAL API LOOKUP (2 mins)

**Skill Definition:**

```yaml
skills:
  - name: apicheck
    description: "Query our internal API documentation"
    type: url
    url: "https://internal-docs.company.com/api/search"
    headers:
      Authorization: "Bearer ${DOCS_API_TOKEN}"
```

**Demo Flow:**

1. Type: `@apicheck how do I authenticate with the payments API?`
2. Show Copilot querying the internal system and returning results

**Talk Track:**

"This skill reaches out to our internal documentation system. Copilot sends the query to our API, gets back the relevant docs, and includes it in the response. Now developers don't context-switch to internal wikis - the answers come right into their IDE."

**Note:** Have a mock endpoint or screenshot ready if live demo isn't feasible.

---

### LIVE SKILL CREATION (6 MINS)

**Setup:**
Walk through creating a simple prompt-based skill from scratch.

---

**Scenario:**

"Let's create a skill that helps developers write commit messages following our team's conventional commit format."

---

**Step 1: Create the file (1 min)**

1. In VS Code, create `.github/skills.yml` in the demo repo
2. Start with the basic structure:

```yaml
skills:
  - name: commitmsg
    description: "Generate conventional commit messages"
    type: prompt
```

**Talk Track:**

"Skills live in `.github/skills.yml` at the root of your repo. You define them as a list under the `skills` key. Each skill needs a name, description, and type."

---

**Step 2: Add the prompt (2 mins)**

```yaml
skills:
  - name: commitmsg
    description: "Generate conventional commit messages"
    type: prompt
    prompt: |
      Generate a commit message using Conventional Commits format:
      
      Format: <type>(<scope>): <subject>
      
      Types: feat, fix, docs, style, refactor, test, chore
      
      Rules:
      - Subject line max 50 characters
      - Use imperative mood ("add" not "added")
      - No period at the end
      - Body wraps at 72 characters if needed
      
      Based on the code changes, generate an appropriate commit message.
```

**Talk Track:**

"The `prompt` field is where we teach Copilot our team's specific requirements. I'm encoding our commit message format rules here once, so everyone follows the same convention."

---

**Step 3: Test the skill (2 mins)**

1. Make a code change in the demo repo
2. Stage the changes
3. Open Copilot Chat
4. Type: `@commitmsg write a commit message for my staged changes`
5. Show the formatted output

**Talk Track:**

"Just like that, we have a working skill. Copilot read the git diff, applied our formatting rules, and generated a compliant commit message. This is the power of skills - codifying team knowledge into reusable commands."

---

**Step 4: Commit and share (1 min)**

1. Commit the `.github/skills.yml` file
2. Push to the repo

**Talk Track:**

"Once this is committed, every developer who pulls this repo gets access to `@commitmsg` automatically. No installation, no configuration. It just works."

---

### BEST PRACTICES (3 MINS)

**SKILL DESIGN PRINCIPLES**

**Keep Skills Focused**

- One skill = one responsibility
- Don't create a mega-skill that does everything
- Example: `@security-scan` not `@checkeverything`

**Write Clear Descriptions**

- Developers see descriptions when they type `@` in Chat
- Be specific about what the skill does
- Example: "Check code against OWASP Top 10" vs "Security stuff"

**Use Descriptive Names**

- Skill names should be intuitive: `@deploy-check`, `@test-data`, `@review-security`
- Avoid abbreviations: `@depl` or `@sec` are unclear

**Test Your Prompts**

- Prompt-based skills are only as good as their instructions
- Test with different code samples
- Refine based on what Copilot returns

---

**PROMPT-BASED SKILL TIPS**

**Be Explicit**

```yaml
# BAD
prompt: "Check for errors"

# GOOD  
prompt: |
  Check this code for:
  - Null pointer exceptions
  - Unhandled promise rejections
  - Missing input validation
  Provide specific line numbers and suggested fixes.
```

**Provide Examples**

```yaml
prompt: |
  Generate test names using this format:
  
  ✅ "test_functionName_whenCondition_thenExpectedBehavior"
  ❌ "test1", "testFunction"
  
  Example: test_login_whenInvalidPassword_thenReturnsError
```

**Set Output Format**

```yaml
prompt: |
  Output your response as:
  
  SUMMARY: One-line overview
  ISSUES: Bullet list
  RECOMMENDATIONS: Numbered list
```

---

**URL-BASED SKILL TIPS**

**Secure Your Endpoints**

- Use authentication tokens
- Store secrets in environment variables: `${TOKEN_NAME}`
- Don't commit credentials to `.github/skills.yml`

**Design Response Format**

- Your API should return structured data (JSON preferred)
- Copilot will format the response for the user
- Include enough context in the response

**Handle Errors Gracefully**

- Return helpful error messages if API fails
- Example: "Could not reach deployment service. Check VPN connection."

**Rate Limiting**

- Be mindful of API limits
- Cache responses when possible on your API side

---

### INTEGRATION WITH OTHER COPILOT FEATURES

**Skills + Copilot Instructions**

"Skills and instructions work together. Instructions provide general repo context. Skills provide specific capabilities."

Example:
- Instruction: "This is a React app using TypeScript"
- Skill: `@component-gen` creates components following your structure

**Skills + Agents**

"Copilot Agents can invoke skills during their reasoning. A deployment agent might use your `@status-check` skill automatically."

**Skills + Chat Context**

"Skills have access to:
- Highlighted code
- Open files
- Chat history
- Git status"

Use this context in your prompts: "Based on the highlighted code..."

---

### Q&A PREP

**Expected Questions:**

**Q: "Where should we define our skills - in every repo or centrally?"**

A: Both patterns work. For team-wide skills (standards, commit formats), create a template repository with `.github/skills.yml` and have devs clone it. For repo-specific skills (deployment commands, domain logic), keep them in that repo.

---

**Q: "Can skills access our production systems?"**

A: URL-based skills can call any API you configure. Use authentication, restrict permissions, and consider read-only endpoints for safety. Skills should query data, not perform destructive actions.

---

**Q: "How do we share skills across multiple repos?"**

A: Currently, skills are per-repository. For shared skills, use:
- Template repositories
- GitHub Actions to sync `.github/skills.yml` across repos
- Maintain a central "skills library" repo teams can copy from

---

**Q: "Can skills execute code or make changes automatically?"**

A: No. Skills provide context and instructions to Copilot, but developers still review and accept suggestions. This maintains safety and control.

---

**Q: "What's the difference between skills and Copilot extensions?"**

A: Skills are lightweight YAML definitions for your organization. Extensions are packaged plugins built by third parties (Sentry, DataDog, etc.) with more complex functionality. Start with skills - they're easier to create and maintain.

---

**Q: "How do we test URL-based skills?"**

A: Build your API endpoint first, test it with curl/Postman, then integrate into the skill. Use environment variables for different environments (staging vs prod APIs).

---

### CLOSING STATEMENT

"Here's the key takeaway: Custom Copilot Skills let you encode your team's unique knowledge directly into the developer workflow. Instead of wikis and Slack threads, your standards and tools become `@commands` that work right where developers code."

"Start simple - create one prompt-based skill for something your team does repeatedly, like code review checklists or documentation templates. Once you see the value, you'll find dozens of opportunities to create skills."

"Skills are how you make Copilot truly yours."

---

## DEMO CHECKLIST

**Before the Demo:**

- [ ] Create `.github/skills.yml` with 2-3 pre-built skills
- [ ] Test each skill in VS Code Copilot Chat
- [ ] Prepare a simple skill to create live (commit message example works well)
- [ ] Have example code ready that violates standards (for demo)
- [ ] If showing URL-based skill, have API endpoint ready or screenshot prepared

**Demo Repository Needs:**

- [ ] Some code with standards violations (for `@standards` demo)
- [ ] An undocumented function (for `@docs` demo)
- [ ] Staged git changes (for `@commitmsg` creation)

---

## ADDITIONAL RESOURCES

- [Copilot Skills Documentation](https://docs.github.com/en/copilot/customizing-copilot/creating-custom-skills)
- [Skills YAML Schema Reference](https://docs.github.com/en/copilot/customizing-copilot/skills-yaml-schema)
- [Example Skills Repository](https://github.com/github/copilot-skills-examples) *(note: check if this exists or use your own)*