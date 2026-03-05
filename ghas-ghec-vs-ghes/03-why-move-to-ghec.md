# Why Move to GHEC — The Security Case

> **Customers:** CoxAuto, Southern Company  
> **Positioning:** GHAS on GHES is excellent — but GHEC unlocks security capabilities you can't get on-prem  
> **Last Updated:** March 2026

---

## The Pitch

**GHAS on GHES gives you a strong security foundation. GHEC takes you further — with AI-powered remediation, faster feature access, and security capabilities that require cloud infrastructure to work.**

The question isn't whether GHAS on GHES is good. It is. The question is: *what are you leaving on the table?*

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

> "You've invested heavily in GHES and GHAS — and you're getting real value from it. But your security team is spending time on manual remediation that Copilot Autofix would handle automatically. Your developers are seeing alerts without suggested fixes. And when new secret types appear, you're waiting quarters for detection to catch up. Moving to GHEC unlocks AI-powered security that turns your GHAS investment from *good* to *best-in-class*."

### Southern Company

> "Compliance and security governance matter enormously in your industry. Security Campaigns on GHEC would let your security team orchestrate remediation company-wide with tracking and accountability — exactly what regulators want to see. And the unbundled licensing on GHEC means you could start with Secret Protection alone if secrets are your top priority, rather than committing to the full GHAS bundle upfront. GHEC doesn't just give you better security tools — it gives you better security *management*."

---

## Addressing the Objection: "We Need On-Prem"

| Concern | Response |
|---|---|
| "Our code can't leave our network" | GHEC with data residency (EU or US) and IP allow lists keeps data controlled. GitHub's SOC 2, FedRAMP (in progress), and ISO 27001 certifications address compliance. |
| "We've invested in GHES infrastructure" | Migration can be incremental — start with new projects on GHEC while maintaining GHES for legacy repos. |
| "Upgrading is disruptive" | That's exactly the point — on GHEC, there are no upgrades. You always have the latest. |
| "We need air-gapped environments" | For truly air-gapped use cases, GHES remains the right choice. But most "on-prem" requirements are actually about control, not isolation — and GHEC provides robust controls. |

---

## Bottom Line

> **"GHAS on GHES protects your code today. GHAS on GHEC protects your code *and* helps you fix it — faster, smarter, and with less manual effort. The longer you stay on GHES-only, the wider the gap gets."**
