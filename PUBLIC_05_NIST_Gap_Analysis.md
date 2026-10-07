# NIST CSF 2.0 Maturity Assessment

## Overview

NIST Cybersecurity Framework 2.0 describes six Functions organizing cybersecurity outcomes. This assessment evaluates HarborPoint's current and target maturity across 22 Subcategories using a project-specific 0–5 scale:

- **0:** Not Implemented
- **1:** Initial (ad-hoc, reactive)
- **2:** Developing (documented, limited consistency)
- **3:** Defined (standardized, repeatable)
- **4:** Managed (metrics-driven, continuous improvement)
- **5:** Optimized (proactive, integrated)

---

## Current vs. Target Maturity

| Function | Current | Target | Gap |
|----------|---------|--------|-----|
| **Govern (GV)** | 1.5 | 2.5 | 1.0 |
| **Identify (ID)** | 1.8 | 3.0 | 1.2 |
| **Protect (PR)** | 2.0 | 3.0 | 1.0 |
| **Detect (DE)** | 1.5 | 2.5 | 1.0 |
| **Respond (RS)** | 1.0 | 2.5 | 1.5 |
| **Recover (RC)** | 1.5 | 2.5 | 1.0 |
| **Overall** | **1.8** | **2.8** | **1.0** |

---

## Govern (GV) — Risk Management & Governance

**Current State: 1.5 (Initial)**  
Policies exist but are not consistently enforced. Risk management is informal. Board and executive engagement is reactive rather than strategic.

**GV.RM (Risk Management Program):**
- Current: 1 (Risk assessment exists but not formalized; findings not tracked to closure)
- Target: 3 (Formal annual risk assessment; risk register; board reporting)
- Gap: Need formalized risk assessment process, board reporting, and risk acceptance documentation

**GV.SC (Supply Chain Risk Management):**
- Current: 1 (No formal vendor risk assessment process)
- Target: 3 (Third-party risk template; vendor SLAs; incident response agreements)
- Gap: Need vendor risk assessment and contract language for data handling and breach notification

**GV.OV (Oversight):**
- Current: 1 (Executive awareness but no formalized governance structure)
- Target: 2 (Regular executive reporting on security metrics and incidents)
- Gap: Establish quarterly security steering committee; executive dashboard

**GV.PO (Policy, Processes & Oversight):**
- Current: 2 (Policies exist: incident response, backup, access control; inconsistently followed)
- Target: 3 (Policies documented, reviewed annually, communicated)
- Gap: Formalize policy exception process; annual review cycle; training

---

## Identify (ID) — Asset & Risk Management

**Current State: 1.8 (Initial/Developing)**  
Asset inventory is partial. Risk assessment is point-in-time, not continuous. Security requirements not integrated into development.

**ID.AM (Asset Management):**
- Current: 2 (Asset inventory exists for endpoints and cloud infrastructure; databases not fully documented)
- Target: 3 (Complete inventory with criticality ratings; data ownership assigned)
- Gap: Extend inventory to applications, SaaS accounts, data stores; document data flows

**ID.RA (Risk Assessment):**
- Current: 1 (Ad-hoc threat assessment; no formal methodology or documentation)
- Target: 3 (Formal annual risk assessment; threat modeling; vulnerabilities tracked)
- Gap: This engagement establishes baseline; next step is annual refresh cycle

---

## Protect (PR) — Access Control & Data Security

**Current State: 2.0 (Developing)**  
Technical controls are partially deployed. Enforcement is inconsistent. Encryption is implemented but audit logging is incomplete.

**PR.AA (Access Management):**
- Current: 2 (MFA optional; some admin accounts password-only; service accounts unmanaged)
- Target: 3 (MFA enforced; JIT provisioning; PAM platform; regular access reviews)
- Gap: MFA enforcement (30 days); secrets management (60 days); PAM evaluation (6 months)

**PR.DS (Data Security):**
- Current: 2 (Encryption at rest enabled; encryption in transit enforced; audit logging incomplete)
- Target: 3 (Consistent encryption; audit logging for all data access; data classification policy)
- Gap: Formalize data classification; enable database audit logging; centralize to SIEM

**PR.IR (Infrastructure Resilience):**
- Current: 1 (Backup system exists; restoration procedures untested; no multi-region failover)
- Target: 3 (Tested backup restoration; documented RTO/RPO; multi-region or alternate recovery)
- Gap: Backup restoration testing (45 days); multi-region evaluation (6 months)

**PR.PS (Platform Security):**
- Current: 2 (Patching quarterly; WAF enabled; S3 encryption at rest; CloudTrail logging partial)
- Target: 3 (Patch management formalized; vulnerability scanning continuous; compliance monitoring)
- Gap: Enable AWS Config compliance; monthly vulnerability scan; patch cycle to 14–30 days

**PR.AT (Awareness & Training):**
- Current: 1 (Annual security training; phishing testing occasional; no role-based training)
- Target: 2 (Role-based training; quarterly phishing simulation; security newsletter)
- Gap: Develop role-specific training for developers, admins, business users; formalize phishing campaign

---

## Detect (DE) — Continuous Monitoring & Analysis

**Current State: 1.5 (Initial)**  
Logging is partial. SIEM is deployed but coverage is incomplete. Alerts are manual. Threat hunting does not occur.

**DE.CM (Continuous Monitoring):**
- Current: 1 (Splunk deployed ~60–70% coverage; CloudTrail enabled; no automated compliance checks)
- Target: 3 (Splunk full coverage; AWS Config rules; vulnerability scanning continuous; alerting automated)
- Gap: Extend SIEM coverage to all systems; implement AWS Config; monthly vulnerability scans

**DE.AE (Detection & Analysis):**
- Current: 1 (Alerts generated; manual investigation; response time 4–24 hours)
- Target: 2 (Escalation procedures documented; response time target 2 hours; playbooks defined)
- Gap: Document alert escalation; establish 2-hour response SLA; develop incident playbooks

---

## Respond (RS) — Incident Response

**Current State: 1.0 (Initial)**  
Incident response plan exists but has not been tested. Roles are not clear. Communication procedures are informal.

**RS.MA (Response Mobilization):**
- Current: 1 (Plan exists; roles not clearly defined; no regular testing)
- Target: 2 (Roles documented; escalation procedures clear; tabletop exercises annual)
- Gap: Tabletop exercise (60 days); update IR plan; establish incident commander role

**RS.MI (Response Mitigation):**
- Current: 1 (Ad-hoc; no established procedures for containment or remediation)
- Target: 2 (Incident playbooks documented; containment procedures clear)
- Gap: Develop playbooks for credential compromise, ransomware, data breach

---

## Recover (RC) — Recovery Planning

**Current State: 1.5 (Initial/Developing)**  
Recovery procedures exist but are untested. RTO/RPO not defined. Recovery testing is reactive.

**RC.RP (Recovery Planning & Processes):**
- Current: 1 (Backup strategy exists; restoration procedures untested; RTO/RPO not measured)
- Target: 3 (Tested recovery procedures; RTO/RPO defined and validated; regular drills)
- Gap: Quarterly backup restoration testing (45 days to establish); annual recovery drill (6 months)

---

## Maturity Summary by Function

**Govern:** Most critical gap. Risk management and governance structure need formalization. **Target: Build risk-to-board reporting; establish governance committee; formalize risk acceptance process.**

**Identify:** Asset inventory incomplete; risk assessment methodology needs to become recurring process. **Target: Complete asset inventory; establish annual risk assessment cycle.**

**Protect:** Largest number of control gaps. Access management (MFA, PAM), data security (audit logging), and infrastructure resilience (backup testing) are primary focus areas. **Target: MFA enforcement, secrets management, backup testing, data classification.**

**Detect:** SIEM exists but coverage incomplete; automated alerting absent. **Target: Extend SIEM coverage; enable AWS Config; establish 2-hour response SLA.**

**Respond:** Incident response plan not tested; lowest maturity. **Target: Tabletop exercise; establish playbooks; clarify roles and escalation.**

**Recover:** Backup systems exist but untested and not integrated with business continuity plan. **Target: Quarterly restoration testing; formal RTO/RPO targets; annual DR drill.**

---

## One-Year Targets

At end of Year 1 (October 2027), target maturity is **2.8 of 5.0** across the organization:

- **GV:** 2.5 (Board risk reporting; formal governance; supply chain risk template)
- **ID:** 3.0 (Complete asset inventory; annual risk assessment; threat modeling)
- **PR:** 3.0 (MFA enforced; secrets management live; backup restoration tested; data classification)
- **DE:** 2.5 (SIEM coverage 85%+; AWS Config rules active; monthly vulnerability scans)
- **RS:** 2.5 (Incident playbooks documented; tabletop exercise completed; response SLA established)
- **RC:** 2.5 (Quarterly backup testing schedule; RTO/RPO validated; recovery runbooks)

This represents movement from **Initial/Developing (1.8) to Defined (2.8)**, focusing on standardization and repeatability without premature optimization.

---

## Investment & Timeline

**Year 1 Budget Estimate:** ~$475K  
- MFA enforcement + training: $15K
- Secrets management platform + implementation: $40K
- Backup restoration testing + runbooks: $20K
- AWS Config + SIEM extension: $60K
- Incident response training + tabletop: $30K
- Third-party risk program: $20K
- Data classification + audit logging: $50K
- Governance structure + board reporting: $25K
- Staffing (additional 0.5 FTE security engineer): $120K
- Vendor assessment + PAM evaluation: $30K
- Contingency (10%): $50K

**Timeframe:** Phased over 12 months (Phases 1–4)

---

**Next: Remediation Roadmap & Executive Summary**
