# Why Buy GHAS on GHES — Value Proposition & Talking Points

> **Customers:** CoxAuto, Southern Company  
> **Context:** Both customers are primarily on GHES and evaluating GHAS — may or may not plan to migrate to GHEC  
> **Last Updated:** March 2026

---

## Key Message

**GHAS on GHES is worth purchasing on its own merits — regardless of any cloud migration plans.** It delivers a comprehensive, production-ready application security platform that replaces or consolidates multiple standalone security tools, integrates directly into the developer workflow, and operates entirely within your on-premises infrastructure.

Whether a customer stays on GHES permanently, plans a gradual move to GHEC, or operates in a hybrid state — **GHAS pays for itself on GHES today.**

---

## Why GHAS on GHES — Even Without Moving to GHEC

### Tool Consolidation
- GHAS replaces **3–5 standalone security tools** (SAST, secret detection, SCA, SBOM generation) with a single integrated platform.
- No additional infrastructure to manage — GHAS runs on the same GHES appliance.
- Unified alert management and triage across code scanning, secrets, and dependencies — one pane of glass.

### Developer Experience
- Security findings surface **in the pull request**, not in a separate dashboard developers never check.
- Developers fix issues **before merge**, not after — shifting security left without changing their workflow.
- No context switching between GitHub and external tools — everything lives where developers already work.

### Cost & Operational Efficiency
- Eliminates license costs for separate SAST, SCA, and secret scanning tools.
- Reduces security team toil — automated scanning, automated PRs for dependency fixes, push protection that prevents secrets from landing.
- Security teams spend time on **policy and governance**, not tool maintenance and integration.

### On-Prem Advantages
- Code never leaves your network — critical for data-sensitive industries.
- Integrates with your existing GHES access controls, SSO, and audit logging.
- GHAS licensing on GHES also prepares teams for a future hybrid or cloud migration — skills, workflows, and configurations transfer directly.

---

## Talking Points — What You Get

### 1. Full-Strength Code Scanning with CodeQL

- CodeQL is the **same engine** on GHES and GHEC — there is no "lite" version.
- Supports **30+ languages** including Java, C/C++, C#, JavaScript/TypeScript, Python, Go, Ruby, Swift, and Kotlin.
- Deep semantic analysis catches real vulnerabilities (SQLi, XSS, auth bypass) that traditional SAST tools miss.
- **Custom CodeQL queries** allow both CoxAuto and Southern Company to encode their own internal security standards and catch organization-specific anti-patterns.
- Integrates directly into the pull request workflow — developers get security feedback before code merges, not after.

### 2. Secret Scanning + Push Protection

- Detects **200+ secret types** from partner providers (AWS, Azure, GCP, Slack, etc.) — no configuration required.
- **Push protection** blocks secrets from entering the repository in the first place — this is a game-changer for compliance.
- **Custom patterns** allow scanning for internal tokens, connection strings, or proprietary secret formats unique to CoxAuto/Southern Company infrastructure.
- Non-provider pattern detection (generic passwords, private keys) is available on GHES 3.15+.
- **Delegated bypass** gives security teams control over who can override push protection and under what conditions.

### 3. Dependabot — Automated Dependency Security

- **Vulnerability alerts** powered by the GitHub Advisory Database — the most comprehensive, community-curated vulnerability source.
- **Automated security updates** generate pull requests to fix known vulnerabilities with a single click.
- **Version updates** keep dependencies fresh and reduce the risk of outdated libraries.
- **Grouped updates** (GHES 3.14+) reduce noise by batching related dependency updates into a single PR.
- **Dependency review action** prevents new vulnerable dependencies from entering through pull requests.

### 4. Supply Chain Transparency

- **Dependency graph** provides full visibility into direct and transitive dependencies.
- **SBOM export** (SPDX format) supports compliance with Executive Order 14028 and customer/regulatory requirements — critical for Southern Company's regulated environment.
- **Dependency submission API** allows integrating non-standard build systems and package managers.

### 5. Security Overview & Governance

- **Organization-level dashboards** give security teams a bird's-eye view of alert status, coverage gaps, and remediation progress.
- **Enterprise-level overview** (improving in 3.17+) aggregates security posture across all organizations.
- Role-based access means security teams see what they need without over-privileging access to code.

---

## Customer-Specific Angles

### CoxAuto

- Large GHES footprint with many development teams → GHAS provides **unified security visibility** across all repos without requiring a separate tool.
- **Replaces fragmented AppSec tooling** — no more juggling Checkmarx/Snyk/etc. alongside GitHub. One platform for code scanning, secrets, and dependencies.
- CodeQL custom queries can encode CoxAuto's internal secure coding standards.
- Push protection and secret scanning provide immediate risk reduction for API keys and service credentials across their microservices architecture.

### Southern Company

- Regulated utility industry → SBOM generation and dependency graph directly support **compliance and audit requirements**.
- **GHAS satisfies NERC CIP and critical infrastructure security mandates** — secret scanning with push protection prevents credential exposure.
- On-premises GHES deployment satisfies data residency and network isolation requirements while still providing best-in-class AppSec tooling.
- Security overview dashboards support reporting to security leadership and compliance teams.
- **GHAS on GHES is audit-ready** — all scanning results, policy enforcement, and bypass decisions are logged and reportable.

---

## Bottom Line

> **"GHAS on GHES is worth buying today — period. It replaces multiple standalone tools, integrates security into the developer workflow, and operates entirely within your infrastructure. Whether you move to GHEC tomorrow, next year, or never — you'll get immediate, measurable security value from GHAS on GHES."**
