# HarborPoint Cybersecurity Risk Assessment
## Enterprise Risk & NIST CSF 2.0 Portfolio

**Portfolio Project:** October 2026  
**Assessment Period:** 1 month  
**Scope:** Mid-market regional bank; 175 employees; $35M revenue; 40,000 customers

---

## Disclaimer

**This is a simulated portfolio project.** HarborPoint Financial Services is a fictional organization created for educational purposes. All systems, findings, metrics, and recommendations are simulated and do not represent a real company or actual security posture.

---

## What This Project Demonstrates

This portfolio documents a cybersecurity risk assessment using:

- **Enterprise risk methodology:** 5×5 likelihood-impact matrix with documented judgment residual analysis
- **NIST Cybersecurity Framework 2.0:** Current vs. Target maturity across all six Functions (Govern, Identify, Protect, Detect, Respond, Recover)
- **Cloud security analysis:** AWS architecture review; IAM, S3, RDS, and network segmentation assessment
- **Identity and access management:** MFA enforcement gaps, service account credential management, privilege access controls
- **Business continuity:** Backup and disaster recovery strategy; RTO/RPO assessment; restoration testing
- **Third-party risk:** Vendor integration and data-handling review
- **Executive communication:** Dashboard design, residual risk prioritization, remediation roadmap

---

## How the Assessment Was Conducted

1. **Asset and threat inventory:** Identified 18 critical assets and mapped threat scenarios specific to financial services
2. **Current state review:** Documented technology environment, security controls, and compliance requirements
3. **Risk scoring:** Applied consistent 5×5 matrix with three distinct risk states — inherent, current residual, and target/post-treatment — to separate existing controls from recommended improvements
4. **NIST maturity assessment:** Evaluated current capability against NIST CSF 2.0 Subcategories (22 categories across 6 Functions)
5. **Gap analysis:** Identified gaps between current and target maturity; prioritized remediation based on risk and feasibility
6. **Remediation roadmap:** Sequenced 23 initiatives over 12 months; estimated budget at ~$475K

---

## Key Findings

**Risk Summary:**
- 10 risks identified and prioritized
- Current residual risk distribution: 4 Critical, 5 High, 1 Moderate
- Critical risks: Incomplete MFA on admin accounts, unencrypted service account credentials, untested backup restoration, ransomware resilience gaps

**Maturity:**
- Current: 1.8 of 5.0 (Initial/Developing stage)
- Target: 2.8 of 5.0 (Defined stage)
- Primary gaps: Disaster recovery testing, privilege access management, cloud logging centralization, third-party risk formalization

**Recommended First Year Priorities:**
1. MFA enforcement on all administrative accounts (30 days)
2. Service account credential migration to secrets management (60 days)
3. Backup restoration testing schedule and runbook (45 days)
4. CloudTrail centralization to SIEM (45 days)
5. Third-party risk assessment template and vendor evaluation (90 days)

---

## What's in This Repository

**Main Documents (15–20 pages):**
- `01_Portfolio_Disclaimer.md` — Simulation disclaimers and scope
- `02_HarborPoint_Scenario.md` — Company profile, business criticality, threat landscape
- `03_Architecture_Summary.md` — Simplified architecture diagram, critical dependencies
- `04_Risk_Methodology.md` — Assessment approach, 5×5 matrix, residual analysis method
- `05_Top_10_Risks.md` — Highest-impact risks with threat analysis, current controls, residual scores
- `06_NIST_CSF_Gap_Analysis.md` — Current vs. Target maturity across NIST Functions
- `07_Remediation_Priorities.md` — Top 10 initiatives with sequencing and budget
- `08_12_Month_Roadmap.md` — Phased remediation plan (Phases 1–4)
- `09_Executive_Dashboard.md` — One-page risk metrics, KPI targets, remediation status
- `10_Executive_Summary.md` — High-level findings and recommendations

**Supporting Files:**
- `Full_Risk_Register.xlsx` — All 20 risks with detailed analysis, NIST mappings, evidence references
- `NIST_CSF_Assessment.xlsx` — Complete maturity assessment against all 22 Subcategories
- `Evidence_Register.xlsx` — 39 simulated evidence items (system configurations, policies, test results) cross-referenced to risks
- `Remediation_Roadmap.xlsx` — 23 initiatives with phases, owners, dependencies, budget

---

## Assessment Approach

### Risk Scoring

Risks are scored using a 5×5 matrix (Likelihood × Impact):

**Likelihood:** Probability of threat exploitation given current controls  
1 = Unlikely (attack requires significant effort or low probability)  
2 = Low (occasional occurrence; requires moderate effort)  
3 = Moderate (plausible exploitation; typical for organizations of this size)  
4 = High (common attack vector in financial services; high probability)  
5 = Almost Certain (active exploitation observed; control gaps significant)

**Impact:** Business consequence if risk materializes  
1 = Minimal (limited data, brief downtime)  
2 = Low (some customer/operational impact)  
3 = Moderate (significant operational impact; customer data exposed; regulatory scrutiny)  
4 = High (severe business disruption; large-scale data exposure; regulatory penalties)  
5 = Severe (complete business disruption; large-scale breach; existential threat to organization)

**Risk Rating:** Likelihood × Impact (1–25 scale)  
- Critical: 16–25  
- High: 8–15  
- Moderate: 4–7  
- Low: 1–3  

**Residual Likelihood:** Adjusted after considering CURRENT control effectiveness. Example: MFA risk is Likelihood 3 (residual, because some MFA is implemented but not enforced everywhere). Recommended MFA enforcement would reduce it to Likelihood 1. Documented judgment—not percentage multipliers. **Three-state model:** Inherent (no controls) → Current Residual (existing controls only) → Target (after recommendations).

### Maturity Model

This project uses a **project-specific 0–5 maturity scale** (separate from NIST CSF):

0 = Not Implemented  
1 = Initial (ad-hoc, reactive)  
2 = Developing (documented processes, limited consistency)  
3 = Defined (standardized, repeatable)  
4 = Managed (metrics-driven, continuous improvement)  
5 = Optimized (proactive, integrated across organization)

NIST CSF 2.0 outcomes are assessed independently and not converted to this scale.

### NIST CSF 2.0 Application

This assessment maps risks and recommendations to 22 official NIST CSF 2.0 Subcategories across six Functions:

- **Govern (GV):** Oversight, governance, policy  
- **Identify (ID):** Asset and risk management  
- **Protect (PR):** Access control, data security, infrastructure resilience  
- **Detect (DE):** Continuous monitoring, analysis  
- **Respond (RS):** Incident response and analysis  
- **Recover (RC):** Recovery planning  

Subcategory identifiers are official NIST designations (e.g., GV.RM, PR.AA, DE.CM).

---

## Key Limitations

- **One-month assessment scope:** Real engagements are typically 2–3 months with on-site interviews
- **Simulated evidence:** All assessment artifacts (scan results, policy reviews, interviews) are simulated
- **No penetration testing:** Assessment is based on architecture review and policy analysis only
- **Single-region AWS:** No multi-region failover; assumptions reflect current state only
- **Partial SIEM coverage:** Splunk estimated at 60–70% system coverage
- **No third-party audit:** Vendor risk assessment is template-based, not audit results

---

## What I Learned

**On Risk Assessment:**
- Residual risk depends entirely on the credibility of control assumptions. Saying "MFA reduces phishing risk to 1" requires actual enforcement; without it, the statement is false.
- Risk scoring becomes arbitrary without clear business impact definitions. "High impact" is meaningless—it must tie to revenue, regulatory penalties, or operational RTO.
- Critical risks are often invisible in "mature" environments because controls obscure assumptions. Backup restoration (untested for 18 months) looks like a "low risk, solved problem" until you quantify the impact of failure.

**On NIST CSF 2.0:**
- The Framework describes outcomes (what the organization should achieve), not controls (how to achieve them). This distinction matters: CSF 2.0 is flexible on implementation but precise on outcomes.
- Maturity assessment works best when separated from CSF mapping. A gap analysis (Current Profile vs. Target Profile) is clearer than forcing a single "maturity score" across different Functions.
- Subcategory identifiers change between framework versions. Always verify against the official NIST publication before including identifiers in published work.

**On Financial Services Risk:**
- Credential compromise and backup resilience are equally critical. For HarborPoint, MFA enforcement is an immediate priority (30-day timeline, high impact per effort), while backup restoration testing is equally urgent from a residual risk perspective (both scored 15 Critical residual).
- Third-party risk is often underestimated because it's handled informally. A single compromised Salesforce instance affects customer data access controls.
- Disaster recovery testing gets deferred. The "we have backups" confidence overrides the discipline to actually validate restoration. Untested backups provide false assurance.

**On Communicating Risk:**
- Executives don't need to see all 20 risks. Top 5–7 drive decision-making; the rest provide context.
- Dashboards lie if they show invented precision (e.g., "73% resilience"). Show trends and status; if you must show a number, make it defensible.
- "Future state" targets must be aligned with business need, not security maturity scales. "Active-active multi-region" for a 175-person bank is overkill; "tested DR failover with runbooks" is sufficient.

---

## How to Use This Repository

**For interviews:**
- Start with the Executive Summary
- Reference top 10 risks and remediation priorities
- Use the NIST gap analysis to discuss maturity assessment methodology
- Be ready to defend risk scores (why Likelihood 4? Why that control reduces it to 2?)

**For hiring managers:**
- The Full Risk Register shows completeness and rigor
- The Evidence Register demonstrates assessment depth
- The Remediation Roadmap shows business-aligned prioritization
- NIST mappings show framework fluency

**For peer review:**
- Critique the risk scoring methodology (is Likelihood justified?)
- Challenge NIST mappings (does this risk belong under this Subcategory?)
- Evaluate control assumptions (is MFA enforcement realistic in this environment?)
- Suggest alternative remediation sequencing

---

## Technologies Referenced

- **Identity:** Microsoft Entra ID, Windows 11, Intune, CrowdStrike Falcon
- **Cloud:** AWS (EC2, RDS, S3, IAM, CloudTrail, CloudWatch, WAF)
- **Data:** PostgreSQL (on-premises and RDS replica), Veeam Backup, EBS snapshots
- **Applications:** Microsoft 365, Salesforce, QuickBooks, GitHub
- **Security:** Splunk Enterprise, Fortinet FortiGate, AWS WAF, Rapid7 Nexpose
- **Third-party:** ADP payroll, Proofpoint email archiving, payment processors

---

## Contact & Feedback

This is a learning portfolio. Questions, critique, or suggestions for improvement are welcome.

---

**Created:** October 2026  
**Framework:** NIST Cybersecurity Framework 2.0  
**Portfolio Focus:** Enterprise risk assessment, NIST maturity analysis, remediation roadmap, executive communication
