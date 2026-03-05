# GHAS Value on GHES Today — Talking Points

> **Customers:** CoxAuto, Southern Company  
> **Context:** Both customers are primarily on GHES and evaluating GHAS  
> **Last Updated:** March 2026

---

## Key Message

**GHAS on GHES delivers a comprehensive, production-ready application security platform today.** Customers do not need to wait for a cloud migration to start securing their code, secrets, and supply chain.

---

## Talking Points

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
- CodeQL custom queries can encode CoxAuto's internal secure coding standards.
- Push protection and secret scanning provide immediate risk reduction for API keys and service credentials across their microservices architecture.

### Southern Company

- Regulated utility industry → SBOM generation and dependency graph directly support **compliance and audit requirements**.
- Secret scanning with push protection aligns with critical infrastructure security mandates.
- On-premises GHES deployment satisfies data residency and network isolation requirements while still providing best-in-class AppSec tooling.
- Security overview dashboards support reporting to security leadership and compliance teams.

---

## Bottom Line

> **"You don't need to wait for GHEC to start securing your code. GHAS on GHES gives you enterprise-grade code scanning, secret protection, and supply chain security — today, inside your own infrastructure."**
