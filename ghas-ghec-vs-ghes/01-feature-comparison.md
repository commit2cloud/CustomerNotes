# GHAS Feature Comparison: GHEC vs GHES

> **Audience:** CoxAuto, Southern Company — GHES-first customers evaluating GHAS  
> **Last Updated:** March 2026  
> **Prepared by:** GitHub Solutions Engineering

---

## At a Glance

GitHub Advanced Security (GHAS) provides a powerful suite of application security tools — but not all capabilities ship simultaneously across GitHub Enterprise Cloud (GHEC) and GitHub Enterprise Server (GHES). Cloud-first development means GHEC customers consistently get new security features first, often quarters ahead of GHES.

---

## Full Feature Comparison

### Code Scanning (CodeQL)

| Capability | GHEC | GHES | Notes |
|---|:---:|:---:|---|
| CodeQL analysis (default & custom queries) | ✅ | ✅ | Full parity |
| Third-party SARIF upload support | ✅ | ✅ | Full parity |
| Code scanning alerts & triage | ✅ | ✅ | Full parity |
| Pull request check integration | ✅ | ✅ | Full parity |
| **Copilot Autofix** (AI-generated fix suggestions) | ✅ | ❌ | Cloud-only; requires Copilot + GHEC infrastructure |
| CodeQL model packs (custom framework support) | ✅ | ✅ | Available on GHES 3.14+ |

### Secret Scanning

| Capability | GHEC | GHES | Notes |
|---|:---:|:---:|---|
| Secret scanning alerts | ✅ | ✅ | Full parity |
| Push protection | ✅ | ✅ | Full parity |
| Custom secret patterns | ✅ | ✅ | Full parity |
| Non-provider patterns (generic secrets) | ✅ | ✅ | Available GHES 3.15+ |
| Validity checks for partner tokens | ✅ | ✅ | Availability depends on GHES version |
| **AI-powered secret detection** (latest models) | ✅ | ⏳ | GHEC gets new models immediately; GHES lags by 1–2 quarters |
| Delegated bypass for push protection | ✅ | ✅ | Available GHES 3.14+ |
| Secret scanning metrics & coverage | ✅ | ⚠️ | Dashboard improvements are cloud-first |

### Dependabot

| Capability | GHEC | GHES | Notes |
|---|:---:|:---:|---|
| Dependabot alerts | ✅ | ✅ | Full parity |
| Dependabot security updates | ✅ | ✅ | Full parity |
| Dependabot version updates | ✅ | ✅ | Full parity |
| Grouped security updates | ✅ | ✅ | Available GHES 3.14+ |
| **Custom auto-triage rules** | ✅ | ⏳ | Cloud-first; GHES availability TBD |
| Dependency review action | ✅ | ✅ | Full parity |

### Supply Chain Security

| Capability | GHEC | GHES | Notes |
|---|:---:|:---:|---|
| Dependency graph | ✅ | ✅ | Full parity |
| SBOM export (SPDX) | ✅ | ✅ | Full parity |
| Dependency submission API | ✅ | ✅ | Full parity |
| Private vulnerability reporting | ✅ | ❌ | Cloud-only |

### Security Overview & Administration

| Capability | GHEC | GHES | Notes |
|---|:---:|:---:|---|
| Organization-level security overview | ✅ | ✅ | Full parity |
| Enterprise-level security overview | ✅ | ⚠️ | GHES catching up in 3.17+ |
| **Security Campaigns** (org-wide remediation) | ✅ | ❌ | Cloud-only; on roadmap for GHES |
| **Advanced dashboard views & trends** | ✅ | ⚠️ | GHEC has richer analytics |
| Security coverage views | ✅ | ⚠️ | Improving in GHES 3.17+ |
| Risk-based alert prioritization | ✅ | ⏳ | Cloud-first rollout |

### Licensing & Packaging

| Capability | GHEC | GHES | Notes |
|---|:---:|:---:|---|
| **GHAS unbundled (Code Security + Secret Protection)** | ✅ | ❌ | GHEC supports purchasing separately since April 2025; GHES remains enterprise-bundled |
| Per-committer licensing | ✅ | ✅ | Full parity |

### Platform & Feature Cadence

| Capability | GHEC | GHES | Notes |
|---|:---:|:---:|---|
| Feature release cadence | Continuous | Quarterly | GHES always 1–2 quarters behind |
| Hotfix/patch availability | Immediate | Patch releases | Requires admin-coordinated upgrade |
| AI/ML feature availability | First | Later (if ever) | AI features depend on cloud infrastructure |

---

## Legend

| Symbol | Meaning |
|:---:|---|
| ✅ | Fully available |
| ⚠️ | Partially available or catching up |
| ⏳ | Planned / on roadmap / lagging |
| ❌ | Not available on this platform |

---

## References

- [About GitHub Advanced Security](https://docs.github.com/en/get-started/learning-about-github/about-github-advanced-security)
- [GHES 3.17 GA Changelog](https://github.blog/changelog/2025-06-03-github-enterprise-server-3-17-is-now-generally-available/)
- [GHAS Feature Chart (josh-ops)](https://josh-ops.com/posts/github-advanced-security-feature-chart/)
- [GitHub Public Roadmap](https://github.com/orgs/github/projects/4247)
