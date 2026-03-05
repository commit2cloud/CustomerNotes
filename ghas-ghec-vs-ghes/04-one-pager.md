# GitHub Advanced Security: GHEC vs GHES — One-Pager

> *Customer-ready leave-behind for EBC / whiteboard conversations*

---

## GHAS: What You Get Today on GHES ✅

| Capability | What It Does |
|---|---|
| **CodeQL Code Scanning** | Finds real vulnerabilities (SQLi, XSS, auth bypass) using deep semantic analysis — directly in pull requests |
| **Secret Scanning** | Detects 200+ secret types and blocks them before they enter your repo with push protection |
| **Custom Patterns** | Scan for your organization's internal tokens, keys, and credential formats |
| **Dependabot** | Automated alerts and PRs for vulnerable dependencies — keeps your supply chain safe |
| **SBOM Export** | Generate Software Bill of Materials for compliance and audit |
| **Security Overview** | Org & enterprise dashboards showing security posture across all repositories |

### ➡️ Bottom Line: GHAS on GHES is a production-ready, enterprise-grade AppSec platform.

---

## What GHEC Unlocks Beyond GHES 🚀

| Feature | Impact | GHES Status |
|---|---|---|
| **Copilot Autofix** | AI generates code fixes for every CodeQL alert — remediate in minutes, not days | ❌ Not available |
| **Security Campaigns** | Orchestrate org-wide remediation with tracking & accountability | ❌ Not available |
| **AI Secret Detection** | Latest detection models deployed immediately — no quarterly wait | ⏳ Lags 1–2 quarters |
| **Dependabot Auto-Triage** | Custom rules to dismiss noise and focus on real risk | ⏳ Cloud-first |
| **Unbundled Licensing** | Buy Code Security or Secret Protection separately — start where you need it | ❌ Bundled only |
| **Continuous Updates** | New features ship weekly, not quarterly — always protected with the latest | ❌ Quarterly releases |

### ➡️ Bottom Line: GHEC closes the gap between finding vulnerabilities and fixing them — with AI.

---

## The Security Maturity Journey

```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                     │
│   GHES + GHAS                    GHEC + GHAS                        │
│   ───────────                    ──────────                         │
│                                                                     │
│   ✅ Find vulnerabilities         ✅ Find vulnerabilities            │
│   ✅ Detect secrets               ✅ Detect secrets (AI-enhanced)    │
│   ✅ Track dependencies           ✅ Track dependencies              │
│   ✅ Block in PRs                 ✅ Block in PRs                    │
│                                   ✅ Auto-generate fixes (Autofix)   │
│   ┌────────────────────┐         ✅ Run remediation campaigns        │
│   │  Manual             │         ✅ Auto-triage alert noise          │
│   │  Remediation        │         ✅ Flexible licensing               │
│   │  Required           │         ✅ Always on latest version         │
│   └────────────────────┘                                            │
│                                                                     │
│   DETECT ──────────────────────► DETECT + REMEDIATE + MANAGE        │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Key Metrics That Matter

| Metric | GHES-Only | With GHEC |
|---|---|---|
| Mean time to remediate CodeQL alerts | Days to weeks | **Minutes** (with Copilot Autofix) |
| Secret detection latency for new types | 1–2 quarters behind | **Same day** |
| Security feature currency | Quarterly upgrades | **Always current** |
| Alert noise from Dependabot | Manual triage | **Auto-triage rules** |
| Remediation tracking | Ad hoc | **Security Campaigns** |

---

## Recommended Next Steps

1. **Today:** Maximize GHAS on GHES — ensure CodeQL, secret scanning with push protection, and Dependabot are enabled across all repositories
2. **Near-term:** Pilot GHEC for new projects to evaluate cloud-first features like Copilot Autofix
3. **Strategic:** Plan incremental migration to GHEC to unlock full GHAS capability and AI-powered security

---

## Talk to Us

Your GitHub Solutions Engineering team can help you:
- Run a **GHAS Proof of Value** on your existing GHES environment
- Set up a **GHEC pilot** alongside your GHES deployment
- Build a **migration roadmap** that fits your compliance and infrastructure requirements

---

> *"GHAS on GHES secures your code. GHAS on GHEC secures your code and helps you fix it — faster, smarter, with AI."*

---

*GitHub Confidential — Prepared for CoxAuto & Southern Company*
