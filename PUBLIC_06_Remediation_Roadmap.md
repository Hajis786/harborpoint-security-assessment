# 12-Month Remediation Roadmap

## Executive Summary

This roadmap prioritizes 23 initiatives across four phases (Q1–Q4 2027) to address the top 10 risks and close NIST CSF 2.0 maturity gaps. Sequencing respects dependencies and resource constraints. 

**Total estimated investment (simulated planning):** ~$475K + 0.5 FTE security engineering  
*Cost estimates are for prioritization and planning purposes. Actual costs depend on vendor pricing, labor rates, and implementation scope.*

---

## Phase 1: Immediate Actions (Months 1–3, ~$115K)

**Objective:** Address critical risks (MFA, service account credentials, ransomware resilience) and establish governance foundation.

| Initiative | Owner | Timeline | Cost | Residual Risk Impact |
|-----------|-------|----------|------|---------------------|
| **1.1: MFA Enforcement on Admin Accounts** | Security Manager | 30 days | $10K | RK-001: Likelihood 4→1 (Critical→Low) |
| **1.2: Service Account Migration to Secrets Management** | Cloud Architect + DBAdmin | 60 days | $40K | RK-002: Likelihood 4→2 (Critical→Moderate) |
| **1.3: Incident Response Plan Review & Tabletop Exercise** | Security Manager | 60 days | $5K | RK-008: Response time improvement |
| **1.4: Backup Restoration Testing Schedule & First Test** | Systems Admin | 45 days | $15K | RK-003: Validates RTO/RPO; establishes trend |
| **1.5: Ransomware Response Playbook** | Security Manager | 45 days | $0K | RK-007: Containment procedures |
| **1.6: Executive Security Steering Committee** | CIO | 30 days | $0K | GV.OV: Governance structure |
| **1.7: Formal Third-Party Risk Assessment Template** | Security Manager | 60 days | $5K | RK-006: Vendor evaluation framework |
| **1.8: EDR Tuning & Alert Escalation** | Security Manager | 30 days | $10K | RK-007: Detection time reduction |
| **1.9: SIEM Alert Rules for High-Risk API Calls** | Splunk Admin | 45 days | $5K | RK-005: CloudTrail alerting |
| **1.10: Data Classification Policy Draft** | Security Manager + Compliance | 45 days | $10K | PR.DS: Foundation for audit logging |

**Phase 1 Outcomes:**
- MFA fully enforced; admin credential compromise risk drops to Low
- Service account credential exposure risk mitigated
- Incident response procedures tested and updated
- Backup restoration validated; quarterly testing schedule established
- Governance committee meets; board reporting initiated

**Dependencies:** None; can execute in parallel

**Risks:** Resistance to MFA enforcement; slow secrets platform adoption

---

## Phase 2: Control Implementation (Months 4–6, ~$145K)

**Objective:** Implement technical controls for cloud security, access management, and logging centralization.

| Initiative | Owner | Timeline | Cost | Residual Risk Impact |
|-----------|-------|----------|------|---------------------|
| **2.1: AWS Config Compliance Rules** | Cloud Architect | 45 days | $15K | RK-004: S3 bucket exposure detection |
| **2.2: CloudTrail Centralization to Splunk** | Cloud Architect + Splunk Admin | 45 days | $30K | RK-005: API activity centralized to SIEM |
| **2.3: Database Audit Logging (PostgreSQL)** | DBAdmin | 60 days | $20K | PR.DS: Access to customer data logged |
| **2.4: PAM Platform Evaluation & POC** | Cloud Architect + Security Manager | 60 days | $30K | RK-010: Privilege access centralization |
| **2.5: Vulnerability Scanning Automation (Monthly)** | Security Manager | 30 days | $10K | PR.PS: Vulnerability discovery frequency |
| **2.6: AWS S3 Bucket Audit & Remediation** | Cloud Architect | 30 days | $5K | RK-004: Bucket policies hardened |
| **2.7: Patch Management Cycle Formalization (14–30 days)** | Systems Admin | 30 days | $10K | PR.PS: Vulnerability window reduction |
| **2.8: Security Awareness Training Program** | Security Manager | 60 days | $15K | PR.AT: Employee baseline knowledge |
| **2.9: Third-Party Vendor Risk Assessments** | Security Manager | 90 days | $5K | RK-006: Vendor control evaluation |
| **2.10: Multi-Region DR Feasibility Study** | Cloud Architect | 45 days | $10K | RK-009: Business case for multi-region |

**Phase 2 Outcomes:**
- AWS environment compliance continuously monitored
- API activity and database access logged to SIEM
- PAM platform evaluated; pilot implementation planned for Phase 3
- Vulnerability discovery automated; patch cycle shortened
- Vendor risk assessments underway
- Security awareness baseline established

**Dependencies:** Phase 1 governance (steering committee approves budget)

**Risks:** Complexity of CloudTrail centralization; PAM vendor selection delay

---

## Phase 3: Enhancement & Testing (Months 7–9, ~$145K)

**Objective:** Implement access management improvements (PAM, JIT provisioning), complete disaster recovery testing, and formalize incident response.

| Initiative | Owner | Timeline | Cost | Residual Risk Impact |
|-----------|-------|----------|------|---------------------|
| **3.1: PAM Platform Implementation (Phase 1)** | Cloud Architect + DBAdmin | 90 days | $50K | RK-010: Privileged access controlled & logged |
| **3.2: Just-in-Time (JIT) Access for Admin Accounts** | Cloud Architect | 60 days | $20K | RK-001/RK-010: Privilege escalation control |
| **3.3: Quarterly Backup Restoration Testing (Q3)** | Systems Admin | 30 days | $10K | RK-003: Trend validation; RTO/RPO confirmed |
| **3.4: Ransomware Simulation Exercise** | Security Manager | 45 days | $15K | RK-007: Incident response readiness test |
| **3.5: Incident Response Playbooks (Finalized)** | Security Manager | 45 days | $10K | RS.MA: Response procedures codified |
| **3.6: Threat Hunting Engagement (Limited)** | Consultant | 30 days | $20K | DE.AE: Advanced detection capability |
| **3.7: Annual Risk Assessment (Formal)** | Security Manager + Consultant | 45 days | $15K | ID.RA: Recurring risk methodology |
| **3.8: SIEM Expansion to Remaining Systems** | Splunk Admin + Systems Admin | 60 days | $15K | DE.CM: SIEM coverage 85%+ |
| **3.9: Phishing Simulation Program (Quarterly)** | Security Manager | 30 days | $5K | PR.AT: Awareness effectiveness measured |
| **3.10: Data Governance Kick-off** | CIO + Compliance Officer | 60 days | $10K | ID.AM: Data ownership clarity |

**Phase 3 Outcomes:**
- PAM platform live; privileged access controlled and audited
- JIT provisioning deployed for high-risk admin accounts
- Backup restoration tested quarterly; RTO/RPO targets validated
- Ransomware response tested end-to-end
- Threat hunting identifies potential persistence mechanisms
- SIEM coverage extended to 85%+ of critical systems
- Data governance program initiated

**Dependencies:** Phase 2 controls implemented; steering committee oversight

**Risks:** Staff turnover during long-duration initiatives; consultant availability

---

## Phase 4: Optimization & Documentation (Months 10–12, ~$70K)

**Objective:** Optimize controls based on testing results, complete documentation, formalize metrics, and prepare for business continuity testing.

| Initiative | Owner | Timeline | Cost | Residual Risk Impact |
|-----------|-------|----------|------|---------------------|
| **4.1: Formal Risk Register Review & Update** | Security Manager | 30 days | $10K | GV.RM: Risk trends documented |
| **4.2: Compliance Verification (FDIC-style)** | Security Manager + Compliance Officer | 60 days | $20K | GV.OV: Regulatory posture assessment |
| **4.3: PAM Phase 2 Expansion (Database & Backup Admins)** | Cloud Architect + DBAdmin | 60 days | $20K | RK-010: Full admin access controlled |
| **4.4: Annual Disaster Recovery Drill** | Systems Admin + Security Manager | 45 days | $10K | RC.RP: Full recovery scenario tested |
| **4.5: Incident Response Tabletop (Annual)** | Security Manager | 30 days | $0K | RS.MA: Continuous readiness |
| **4.6: Security Metrics Dashboard (Finalized)** | Security Manager | 30 days | $5K | GV.RM: Executive visibility |
| **4.7: Policy Review & Annual Update Cycle** | CIO + Security Manager | 45 days | $5K | GV.PO: Governance formalization |
| **4.8: Lessons Learned & Program Assessment** | Security Manager | 45 days | $0K | Overall: Continuous improvement |
| **4.9: Year 2 Risk Assessment & Planning** | Security Manager + Consultant | 30 days | $0K | GV.RM: Forward planning |
| **4.10: Staff Training on Mature Controls** | Security Manager | 30 days | $0K | PR.AT: Role-based training on new tools |

**Phase 4 Outcomes:**
- Risk register formalized; quarterly review cycle established
- Compliance posture assessed against FDIC expectations
- Full admin access (database, backup, cloud) managed through PAM
- Disaster recovery tested; RTO/RPO validated end-to-end
- Security metrics dashboard live; board reporting automated
- Policies reviewed; exception process documented
- Year 2 roadmap drafted based on lessons learned

**Dependencies:** All Phase 1–3 initiatives completed

**Risks:** Fatigue from ongoing initiatives; resource constraints end of year

---

## Resource Requirements

| Resource | Year 1 Allocation | Notes |
|----------|-----------------|-------|
| **Security Manager** | 60% | Drives initiative execution; governance |
| **Cloud Architect** | 40% | AWS Config, CloudTrail, PAM, multi-region study |
| **DBAdmin** | 20% | Backup testing, audit logging, PAM integration |
| **Systems Admin** | 30% | Backup testing, patching, SIEM expansion |
| **Splunk Admin** | 20% | SIEM rules, centralization, alerting |
| **External Consultant** | 2 months (~$40K) | Threat hunting, risk assessment, tabletop facilitation |
| **Additional FTE (0.5)** | 12 months (~$120K) | Security engineer for ongoing control hardening |

**Total Year 1 Investment:** ~$475K (including staffing)

---

## Success Metrics

**Q1 (90 days):**
- ✅ MFA enforced on 100% of admin accounts
- ✅ First backup restoration test completed; RTO measured
- ✅ Steering committee meeting established (quarterly)

**Q2 (180 days):**
- ✅ Service account credentials migrated (80% complete)
- ✅ AWS Config compliance rules active; 3+ months of data
- ✅ Incident response plan updated; tabletop completed

**Q3 (270 days):**
- ✅ CloudTrail centralized to Splunk; alerting rules active
- ✅ Database audit logging enabled for 90% of customer data access
- ✅ PAM pilot running; 2+ weeks of audit logs

**Q4 (360 days):**
- ✅ All Phase 1–2 initiatives complete; Phase 3 90% complete
- ✅ NIST maturity re-assessment: Current 2.5+ of 5.0
- ✅ Risk register updated; quarterly review cycle established

---

## Risk of Not Executing

| Risk | Current State | Without Roadmap | With Roadmap |
|------|---------------|-----------------|--------------|
| **Credential Compromise** | Likelihood 4 (High) | Remains 4 | Reduced to 1 (Low) by Q1 |
| **Ransomware Impact** | Likelihood 3 (Moderate) | Remains 3–4 | Reduced to 2 by Q2 via detection |
| **Backup Restoration Failure** | Unknown RTO/RPO | Potential data loss | Validated quarterly; predictable recovery |
| **Regulatory Findings** | Likely in next FDIC exam | FDIC findings; remediation orders | Remediation roadmap demonstrates response |

Recommendation: **Execute Phase 1 immediately; commit to full roadmap within Q1.**

---

**Next: Executive Summary & Dashboard**
