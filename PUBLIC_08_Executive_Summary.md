# Executive Summary

**Assessment Engagement:** October 2026  
**Assessment Period:** 1 month (simulated)  
**Organization:** HarborPoint Financial Services (175 employees, $35M revenue, 40,000 customers)  
**Assessment Framework:** NIST Cybersecurity Framework 2.0

---

## Key Findings

### Current Security Posture: **1.8 of 5.0 (Initial/Developing)**

HarborPoint's security controls are **partially deployed** across the organization. Technical controls (MFA, encryption, backup, SIEM) exist but are **inconsistently enforced** and **not fully integrated**. Governance structures are **informal**, and incident response procedures are **untested**. The organization is in an **active growth phase** with expanding cloud adoption, creating both opportunity to improve controls and risk of misconfiguration.

### Assessment Scope: Three Domains

1. **External/Customer Domain** — Internet-facing customer portal (40,000 users) and mobile access
2. **Enterprise Domain** — Internal employee systems (160 Windows 11 devices), Microsoft Entra ID identity, AWS cloud infrastructure
3. **Data Domain** — PostgreSQL primary database (on-premises), Veeam backup system, S3 archival, third-party integrations (Salesforce, ADP, payment processor)

---

## Critical Risks (Current Residual Score 15+)

| Risk | Current Residual Score | Business Impact | Mitigation Timeline |
|------|-----------------|-----------------|-------------------|
| **RK-001: Incomplete MFA** | 15 (Critical) | Credential compromise; admin account takeover; lateral movement to databases; data breach | 30 days (Phase 1) |
| **RK-002: Service Account Credentials in Config Files** | 16 (Critical) | Unencrypted credentials in repositories; broad database access; ransomware lateral movement | 60 days (Phase 1) |
| **RK-003: Untested Backup Restoration** | 15 (Critical) | Complete data loss; business continuity failure; regulatory non-compliance; revenue loss | 45 days (Phase 1) |
| **RK-007: Ransomware Attack on Portal & Databases** | 15 (Critical) | Business disruption; payment processing halt; extended recovery window if backup untested; regulatory penalties | 45 days (Phase 1) |

**Key Insight:** All four critical risks are Phase 1 priorities. RK-001 and RK-002 are quick wins (30–60 days) with high leverage. RK-003 and RK-007 require complementary controls (backup testing + ransomware response playbooks).

---

## High-Risk Findings (Current Residual Score 8–12)

| Risk | Category | Current Residual Score | Root Cause | Quick Fix | Full Remediation |
|------|----------|-----------|-----------|-----------|-----------------|
| **RK-004: S3 Bucket Misconfiguration** | Cloud Security | 12 (High) | No continuous compliance monitoring | AWS Config rules (manual audit) | 30-day Phase 2 |
| **RK-005: CloudTrail Logs Not Centralized to SIEM** | Logging & Monitoring | 12 (High) | CloudTrail enabled; logs not forwarded to Splunk | Splunk forwarder setup | 45-day Phase 2 |
| **RK-006: Third-Party Vendor Risk** | Vendor Management | 8 (High) | Informal vendor risk assessment | Risk assessment template | 90-day Phase 2 |
| **RK-008: Incident Response Plan Not Tested** | Incident Response | 8 (High) | Plan exists; no documented tabletop exercises | Schedule tabletop | 60-day Phase 1 |
| **RK-010: Privilege Access Management (PAM) Gap** | Privileged Access | 8 (High) | Manual privilege management; no audit trail | PAM platform evaluation POC | 90-day Phase 3 |

---

## NIST CSF 2.0 Maturity Assessment

Current maturity is **1.8 of 5.0 (Initial/Developing)**. This means HarborPoint has documented some controls and procedures, but they are **not consistently applied or verified**. Processes are **reactive** rather than proactive.

| Function | Current | Target (Year 1) | Primary Gap |
|----------|---------|-----------------|------------|
| **Govern (GV)** | 1.5 | 2.5 | Risk management informal; governance structure missing |
| **Identify (ID)** | 1.8 | 3.0 | Asset inventory incomplete; risk assessment ad-hoc |
| **Protect (PR)** | 2.0 | 3.0 | Access control inconsistent; audit logging incomplete |
| **Detect (DE)** | 1.5 | 2.5 | SIEM coverage incomplete; automated alerting absent |
| **Respond (RS)** | 1.0 | 2.5 | Incident response plan untested; roles unclear |
| **Recover (RC)** | 1.5 | 2.5 | Backup system exists; restoration procedures untested |

**One-Year Goal:** Reach **2.8 of 5.0 (Defined)** — achieve standardized, documented, repeatable processes with consistent enforcement.

---

## Remediation Investment & Timeline

**Total Year 1 Budget: ~$475K (Simulated Planning Estimates)**
*Note: These are simulated planning estimates for prioritization. Actual costs depend on vendor selection, labor rates, and implementation approach.*
- Tools & services: ~$155K (secrets platform, PAM evaluation, AWS Config, SIEM expansion, vulnerability scanning)
- External services: ~$40K (consultant: threat hunting, risk assessment, tabletop facilitation)
- Staffing (additional 0.5 FTE security engineer): ~$120K
- Staff time reallocation (Security Mgr, Cloud Architect, DBAdmin, Systems Admin, Splunk Admin): ~$160K

**Phased Approach (12 Months):**

- **Phase 1 (Months 1–3, $115K):** Immediate actions — MFA enforcement, backup testing, incident response planning, SIEM alerts, governance structure establishment
- **Phase 2 (Months 4–6, $145K):** Control implementation — AWS Config, CloudTrail centralization, database audit logging, PAM evaluation, vulnerability scanning, vendor assessment
- **Phase 3 (Months 7–9, $145K):** Enhancement & testing — PAM implementation, JIT access, threat hunting, SIEM expansion, phishing simulation, data governance
- **Phase 4 (Months 10–12, $70K):** Optimization — risk register formalization, compliance verification, annual disaster recovery drill, metrics dashboard, Year 2 planning

**Success Metric:** At end of Year 1, NIST maturity moves from 1.8 to 2.8 (Initial→Defined).

---

## Top Recommendations (Priority Sequence)

### Immediate (Next 30 Days)
1. **Enforce MFA on all administrative accounts** — Current residual likelihood 3 (partial MFA) → Target 1 (full enforcement); eliminates credential-only attacks on admin accounts
2. **Establish Executive Security Steering Committee** — Enable budget approval, risk acceptance, governance oversight
3. **Schedule backup restoration test** — Validate RTO/RPO against business requirements; identify restoration gaps

### Short-Term (Next 60 Days)
4. **Migrate service account credentials to secrets management platform** — Implement AWS Secrets Manager; establish 90-day rotation policy
5. **Conduct ransomware tabletop exercise** — Test incident response plan; identify role gaps; codify containment procedures
6. **Tune EDR (CrowdStrike) alert rules** — Reduce alert noise; establish 30-minute escalation SLA for critical alerts

### Medium-Term (Next 90 Days)
7. **Centralize CloudTrail logs to Splunk** — Enable real-time alerting on high-risk API calls (IAM changes, S3 public access grants)
8. **Evaluate PAM platform options** — CyberArk, Delinea, or equivalent; conduct POC (60–90 days)
9. **Develop third-party vendor risk assessment template** — Evaluate Salesforce, ADP, payment processor; establish SLAs and incident response agreements

### Q2 & Beyond (Months 4–12)
10. **Implement AWS Config compliance rules** — Continuous monitoring of S3 bucket policies, IAM permissions, encryption status
11. **Enable database audit logging** — Log all access to customer PII; centralize to SIEM
12. **Formalize quarterly backup restoration testing schedule** — Establish quarterly cadence; document RTO/RPO trends; validate recovery runbooks

---

## Regulatory Alignment

HarborPoint is subject to FDIC safety-and-soundness examination, state banking regulation, GLBA (data protection), and FFIEC guidance (IT security). The remediation roadmap directly addresses FDIC examination expectations:

- **Risk Management:** Formalized annual risk assessment with board reporting (GV.RM)
- **Access Controls:** MFA enforcement, PAM implementation, privileged access audit (PR.AA)
- **Incident Response:** Tested incident response plan with defined escalation (RS.MA)
- **Backup & Disaster Recovery:** Quarterly restoration testing with validated RTO/RPO (RC.RP)
- **Third-Party Risk:** Formal vendor risk assessment and incident response agreements (GV.SC)
- **Compliance Monitoring:** Continuous AWS Config rules, SIEM alerting, vulnerability scanning (DE.CM)

The roadmap is **not** a compliance audit; it is a **business-driven** remediation strategy that happens to align with regulatory expectations.

---

## Risk of Not Executing

| Scenario | Current State | Without Roadmap | With Roadmap |
|----------|---------------|-----------------|--------------|
| **Credential Compromise (Phishing/Spray)** | Likelihood 4 (High) | Admin account takeover; lateral movement to databases | MFA enforcement reduces likelihood to 1 by Week 4 |
| **Ransomware Incident** | Likelihood 3 (Moderate); Response untested | Uncontrolled encryption; extended recovery; revenue loss | EDR tuning + tested response playbook; containment within 30 min by Q1 |
| **Backup Failure** | Unknown RTO/RPO | Permanent data loss; regulatory non-compliance | Quarterly testing validates recovery; RTO measured and predictable by Week 6 |
| **S3 Bucket Exposure** | Likelihood 3 (Moderate) | Customer PII exposure; breach notification; FDIC finding | AWS Config + monthly audit; misconfiguration detected within 24 hours by Q2 |
| **FDIC Examination Finding** | Likely (based on industry trends) | Remediation orders; regulatory penalties; reputational damage | Remediation roadmap demonstrates proactive response; reduces severity of findings |

---

## Organizational Readiness

**Strengths:**
- Cloud infrastructure exists (AWS, Entra ID) — foundation is modern
- SIEM (Splunk) deployed — monitoring foundation in place
- Endpoint detection (CrowdStrike) active — malware detection baseline
- Leadership awareness — CIO engagement, Board interest

**Constraints:**
- Limited security staff (Security Manager @ 60% allocation) — resource constraint for Phase 1 execution
- Vendor dependencies (secrets platform, PAM evaluation) — 60–90 day procurement cycles
- Staff turnover risk — long-duration initiatives (PAM, threat hunting) vulnerable to attrition
- Budget approval process — $475K Year 1 investment requires board approval and phased funding

**Recommendation:** Execute Phase 1 immediately (30–45 days to visible progress). Secure Phase 1 budget approval first (recommended: $115K); submit Phase 2 budget (additional $145K) by end of Q1 based on Phase 1 learnings.

---

## Board-Level Recommendations

**Vote to Approve:**
1. Establishment of Executive Security Steering Committee (monthly oversight, risk acceptance authority)
2. Year 1 remediation roadmap execution (4-phase approach; ~$475K total investment — simulated planning estimates for prioritization)
3. Staffing plan (additional 0.5 FTE security engineer; reallocation of existing staff to remediation)
4. Risk acceptance for High/Moderate risks during Phase 1 (explicitly documented; quarterly review)

**Expected Outcomes (12 Months):**
- NIST CSF maturity: 1.8 → 2.8 (Initial → Defined)
- Critical risks reduced: 4 → 1–2 (RK-001, RK-002, RK-003, RK-007 mitigated to High/Moderate by end of Phase 1)
- High risks reduced: 5 → 2–3 (remaining High risks require Phase 2+ investments)
- Incident response capability: Untested → Tabletop-validated
- Backup resilience: Unknown → Quarterly-tested (RTO/RPO validated)
- Regulatory posture: Reactive → Proactive (formal risk management, board reporting)

---

**Questions for Board Discussion:**

1. Does the Board approve the $475K Year 1 remediation budget?
2. Does the Board authorize the CIO to establish the Executive Security Steering Committee and delegate risk acceptance authority?
3. What is the Board's risk tolerance for the 12-month transition period? Are interim risk acceptance levels (e.g., deferring multi-region failover) acceptable?
4. Should Year 2 planning begin in Q3 2027 to identify strategic investments (e.g., multi-region failover business case, enhanced threat hunting)?

---

**Prepared by:** Security Assessment Team  
**Assessment Framework:** NIST Cybersecurity Framework 2.0  
**Recommended Review Cycle:** Quarterly (Board Risk Committee); Annual (Full Board)
