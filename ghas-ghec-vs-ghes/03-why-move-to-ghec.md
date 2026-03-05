# Why Move to GHEC (or Go Hybrid) — The Security Case

> **Customers:** CoxAuto, Southern Company  
> **Positioning:** GHAS on GHES delivers real value today — GHEC (or a hybrid model) unlocks additional security capabilities you can't get on-prem alone  
> **Last Updated:** March 2026

---

## The Pitch

**GHAS on GHES gives you a strong security foundation — and it's worth purchasing on its own.** But GHEC takes you further with AI-powered remediation, faster feature access, and security capabilities that require cloud infrastructure.

Many customers don't need to choose one or the other. A **hybrid approach** — running GHES for existing workloads and GHEC for new projects or cloud-ready teams — lets you capture the best of both worlds while building toward a long-term cloud strategy.

The question isn't whether GHAS on GHES is good. It is. The question is: *what additional value can you unlock, and how quickly do you want it?*

---

## What You're Missing on GHES

### 1. Copilot Autofix — AI-Powered Vulnerability Remediation

**The single most impactful GHEC-only GHAS feature.**

- When CodeQL finds a vulnerability, Copilot Autofix generates a **ready-to-commit fix** with a natural language explanation.
- Reduces mean-time-to-remediation from days/weeks to **minutes**.
- Developers don't need to be security experts — the fix is presented in their pull request, in context.
- Early data shows **Copilot Autofix resolves 3x more alerts** than manual remediation alone.
- **This feature requires cloud infrastructure** (LLM processing) and is not on the GHES roadmap in the near term.

> *"Imagine every CodeQL alert coming with a suggested fix. That's Copilot Autofix — and it only works on GHEC."*

### 2. Security Campaigns — Org-Wide Remediation at Scale

- Security teams can create **campaigns** to drive coordinated remediation of specific vulnerability classes across the entire organization.
- Track progress, assign ownership, and measure completion — all from the security overview.
- Turns security alerts from a backlog into a **managed program**.
- Critical for large organizations like CoxAuto (many teams, many repos) and Southern Company (compliance-driven remediation).
- **Cloud-only today.** On roadmap for GHES, but no confirmed timeline.

> *"Security Campaigns let your security team run remediation like a project, not a fire drill."*

### 3. AI-Powered Secret Detection — Latest Models, Fastest Response

- GHEC receives new AI detection models **immediately** upon release.
- GHES lags by **1–2 full quarters** — meaning new secret types go undetected on-prem for months.
- In a landscape where new credential types and token formats emerge constantly, detection latency = exposure window.

### 4. Custom Auto-Triage for Dependabot

- GHEC customers can create **custom rules** to automatically dismiss, snooze, or prioritize Dependabot alerts based on context (reachability, environment, CVSS, etc.).
- Dramatically reduces **alert fatigue** — a top complaint from development teams.
- Cloud-first feature; GHES availability is uncertain.

### 5. Flexible Licensing: Code Security + Secret Protection (Unbundled)

- On GHEC, GHAS has been **unbundled** into two purchasable products: Code Security and Secret Protection.
- Customers can start with just what they need — reducing upfront cost and making adoption easier.
- GHES still requires the full **enterprise GHAS bundle** — all or nothing.

### 6. Continuous Feature Cadence

- GHEC receives features **continuously** — multiple times per week.
- GHES releases **quarterly**, and each release requires an admin-coordinated upgrade.
- This means GHES customers are always **3–6 months behind** on the latest security capabilities.
- In application security, being behind on tooling means being behind on protection.

---

## The Narrative for Each Customer

### CoxAuto

> "You've invested heavily in GHES and GHAS — and you're getting real value from it. That investment is sound regardless of what comes next. But your security team is spending time on manual remediation that Copilot Autofix would handle automatically. Your developers are seeing alerts without suggested fixes. You don't need to rip and replace — start by pointing new projects at GHEC to get AI-powered security, while your existing GHES repos keep running with full GHAS protection. Over time, you'll naturally consolidate where it makes sense."

### Southern Company

> "Compliance and security governance matter enormously in your industry. GHAS on GHES already gives you the code scanning, secret protection, and SBOM capabilities your auditors need — and that's worth investing in today. But Security Campaigns on GHEC would let your security team orchestrate remediation company-wide with tracking and accountability — exactly what regulators want to see. A hybrid model lets you keep regulated code on GHES while gaining cloud-first governance tools on GHEC for your modernization projects."

---

## The Hybrid Model: GHES + GHEC Together

For customers who aren't ready for a full migration, a hybrid deployment delivers immediate incremental value:

### How It Works

| Workload | Platform | Why |
|---|---|---|
| Legacy/regulated applications | **GHES** | Stays on-prem, satisfies data residency, continues with existing GHAS coverage |
| New projects & greenfield development | **GHEC** | Gets Copilot Autofix, Security Campaigns, latest features from day one |
| Cloud-native / microservices | **GHEC** | Natural fit for cloud platform; benefits from continuous feature delivery |
| Inner source / shared libraries | **GHEC** | Easier cross-org collaboration + cloud-first security tooling |

### Benefits of Hybrid

- **No big-bang migration required** — move at your own pace, project by project.
- **GHAS skills transfer directly** — CodeQL queries, secret patterns, Dependabot configs all work the same on both platforms.
- **Security teams get a unified view** — Security Overview works across both GHES and GHEC organizations (via EMU or linked enterprise accounts).
- **Test GHEC cloud features with real workloads** before committing to full migration.
- **Budget flexibility** — keep GHES for what needs to stay on-prem, invest in GHEC for what benefits from cloud.

### Hybrid-Specific Angles by Customer

**CoxAuto:**
> "Start by moving two or three new microservices teams to GHEC. They'll immediately get Copilot Autofix and see the remediation speed difference. Meanwhile, your existing GHES repos keep running with full GHAS coverage. It's a low-risk way to prove the value before going broader."

**Southern Company:**
> "Keep your regulated SCADA/OT-adjacent code on GHES where it belongs. But for your IT modernization projects and cloud-first apps, GHEC gives you Security Campaigns for compliance tracking and unbundled licensing to control costs. You don't have to choose — you can run both."

---

## Addressing the Objection: "We Need On-Prem"

| Concern | Response |
|---|---|
| "Our code can't leave our network" | GHEC with data residency (EU or US) and IP allow lists keeps data controlled. GitHub's SOC 2, FedRAMP (in progress), and ISO 27001 certifications address compliance. |
| "We've invested in GHES infrastructure" | That investment isn't wasted. Run hybrid — keep GHES for what needs it, add GHEC for new projects. GHAS configs and skills transfer directly. |
| "Upgrading is disruptive" | That's exactly the point — on GHEC, there are no upgrades. You always have the latest. Hybrid lets you stop upgrading for new projects immediately. |
| "We need air-gapped environments" | For truly air-gapped use cases, GHES remains the right choice. But most "on-prem" requirements are actually about control, not isolation — and GHEC provides robust controls. |

---

## Bottom Line

> **"GHAS on GHES protects your code today — and it's a smart investment right now. Adding GHEC (even in a hybrid model) gives you AI-powered fixes, faster feature access, and security management capabilities you can't get on-prem alone. You don't have to choose one or the other — start where you are, and grow into the cloud at your pace."**
