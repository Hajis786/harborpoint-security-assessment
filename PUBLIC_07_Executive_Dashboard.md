# Executive Dashboard — Security Posture & Remediation Progress

**Assessment Date:** October 2026  
**Target Completion:** December 2027  
**Overall Risk Status:** 🔴 **Critical** (1 Critical residual risk; 8 High residual risks; 1 Moderate residual risk)

---

## Maturity Overview

| Function | Current | Target (Year 1) | Gap | Status |
|----------|---------|-----------------|-----|--------|
| **Govern (GV)** | 1.5 | 2.5 | 1.0 | 🔴 Behind |
| **Identify (ID)** | 1.8 | 3.0 | 1.2 | 🔴 Behind |
| **Protect (PR)** | 2.0 | 3.0 | 1.0 | 🟡 At Risk |
| **Detect (DE)** | 1.5 | 2.5 | 1.0 | 🔴 Behind |
| **Respond (RS)** | 1.0 | 2.5 | 1.5 | 🔴 Highest Gap |
| **Recover (RC)** | 1.5 | 2.5 | 1.0 | 🔴 Behind |
| **Overall** | **1.8** | **2.8** | **1.0** | **🔴 Critical Gap** |

---

## Top 10 Risks — Residual Scores & Remediation Timeline

| Risk | Current Residual Score | Priority | Phase Target | Owner | Notes |
|------|-----------------|----------|---------------|-------|-------|
| **RK-002: Service Account Credentials** | 16 (Critical) | P1 | Phase 1 (60d) | Cloud Arch + DBAdmin | Secrets platform; 90-day rotation policy |
| **RK-001: Incomplete MFA** | 15 (High) | P1 | Phase 1 (30d) | Security Mgr | Quick win; highest impact per effort; eliminates credential attacks |
| **RK-003: Untested Backup** | 15 (High) | P1 | Phase 1 (45d) | Systems Admin | Quarterly testing schedule; RTO/RPO validation |
| **RK-007: Ransomware Attack** | 15 (High) | P1 | Phase 1 (45d) | Security Mgr | EDR tuning, SIEM alerting, response playbooks |
| **RK-004: S3 Misconfiguration** | 12 (High) | P2 | Phase 2 (30d) | Cloud Arch | AWS Config rules; automated compliance checks |
| **RK-005: CloudTrail Gap** | 12 (High) | P2 | Phase 2 (45d) | Cloud Arch + Splunk Admin | Centralize logs; alerting on high-risk API calls |
| **RK-006: Vendor Risk** | 8 (High) | P2 | Phase 2 (90d) | Security Mgr | Assessment template; SLAs; incident response agreements |
| **RK-008: IR Plan Not Tested** | 8 (High) | P1 | Phase 1 (60d) | Security Mgr | Tabletop exercise; playbooks; role clarity |
| **RK-010: PAM Gap** | 8 (High) | P3 | Phase 3 (90d) | Cloud Arch + DBAdmin | Platform evaluation and POC; JIT provisioning |
| **RK-009: Multi-Region Failover** | 5 (Moderate) | P4 | Phase 3 (45d) | Cloud Arch | Business case; defer unless RTO < 2h; acceptable interim risk |

---

## Phase Progress & Key Milestones

### Phase 1: Immediate Actions (Months 1–3)
**Budget: $115K | Status: Ready to Launch**

- [ ] MFA Enforcement (30 days) — **Day 1 Priority**
- [ ] Backup Restoration Testing (45 days) — **Critical path**
- [ ] Service Account Migration (60 days) — Parallelize with MFA
- [ ] Incident Response Tabletop (60 days) — Engage Security Mgr
- [ ] Ransomware Playbook (45 days) — Codify response procedures
- [ ] EDR Tuning (30 days) — CrowdStrike alert rules
- [ ] SIEM Alerts for High-Risk API Calls (45 days) — CloudTrail integration
- [ ] Steering Committee Established (30 days) — CIO to initiate

### Phase 2: Control Implementation (Months 4–6)
**Budget: $145K | Status: Dependent on Phase 1**

- [ ] AWS Config Compliance Rules (45 days)
- [ ] CloudTrail Centralization (45 days)
- [ ] Database Audit Logging (60 days)
- [ ] PAM Platform Evaluation (60 days)
- [ ] Vulnerability Scanning Automation (30 days)
- [ ] Security Awareness Program (60 days)
- [ ] Vendor Risk Assessments (90 days)

### Phase 3: Enhancement & Testing (Months 7–9)
**Budget: $145K | Status: Blocked until Phase 2 complete**

- [ ] PAM Implementation (90 days)
- [ ] JIT Access Deployment (60 days)
- [ ] Quarterly Backup Testing (30 days)
- [ ] Ransomware Simulation Exercise (45 days)
- [ ] Threat Hunting Engagement (30 days)
- [ ] Annual Risk Assessment (45 days)

### Phase 4: Optimization & Documentation (Months 10–12)
**Budget: $70K | Status: Blocked until Phase 3 complete**

- [ ] Risk Register Review & Update (30 days)
- [ ] Compliance Verification (60 days)
- [ ] PAM Phase 2 Expansion (60 days)
- [ ] Annual Disaster Recovery Drill (45 days)
- [ ] Security Metrics Dashboard (30 days)

---

## Resource Allocation & Staffing

| Role | FTE | Year 1 Cost | Key Responsibilities |
|------|-----|-----------|----------------------|
| **Security Manager** | 0.60 | ~$72K | MFA enforcement, incident response, risk assessment, governance |
| **Cloud Architect** | 0.40 | ~$48K | AWS Config, CloudTrail, PAM evaluation, multi-region study |
| **Database Admin** | 0.20 | ~$24K | Backup testing, audit logging, PAM integration |
| **Systems Admin** | 0.30 | ~$36K | Backup testing, patching, SIEM expansion |
| **Splunk Admin** | 0.20 | ~$24K | SIEM rules, centralization, alerting |
| **Additional Security Engineer (NEW)** | 0.50 | ~$120K | Control hardening, ongoing implementation support |
| **External Consultant** | 2 months | ~$40K | Threat hunting, risk assessment, tabletop facilitation |

**Total Year 1 Staffing: ~$364K**  
**Total Year 1 Investment (Tools + Staffing): ~$475K**

---

## Critical Success Factors

1. **Q1 Execution Discipline:** MFA and backup testing must complete on schedule; delays cascade to Phase 2.
2. **Steering Committee Engagement:** Executive oversight mandatory; budget approval, conflict resolution, risk acceptance.
3. **Vendor Responsiveness:** PAM and secrets platform evaluation dependent on vendor timelines (60–90 days for POC).
4. **Staff Retention:** Long-duration initiatives (PAM, threat hunting) require continuity; turnover risk in Q3–Q4.
5. **Tooling Integration:** CloudTrail → Splunk, AWS Config → SIEM, database → audit logging; integration complexity underestimated historically.

---

## Risk Acceptance & Board Reporting

| Risk | Current Posture | Acceptance Decision | Escalation |
|------|-----------------|-------------------|------------|
| **Untested Backups** | Unacceptable | Remediate by end of Phase 1 | Board approval required if delayed past 45 days |
| **MFA Gaps** | Unacceptable | Enforce by end of Phase 1 (30 days) | Board approval required if delayed past 30 days |
| **CloudTrail Centralization** | Acceptable (Interim) | Remediate by end of Phase 2 | Quarterly reporting to board during interim |
| **Multi-Region Failover** | Acceptable (Long-term) | Evaluate Phase 3; defer if cost > business case | Annual business case review; document acceptance |
| **Vendor Risk** | Acceptable (Interim) | Implement Phase 2 assessment process | Quarterly board update on vendor posture |

---

## Success Metrics (Quarterly)

### Q1 (90 days)
- ✅ MFA enforced on 100% of admin accounts
- ✅ First backup restoration test completed; RTO measured
- ✅ Steering committee established; first meeting held
- ✅ Service account migration 50% complete

### Q2 (180 days)
- ✅ Service account credentials migrated (80% complete)
- ✅ AWS Config compliance rules active; 90+ days of data
- ✅ Incident response tabletop completed; findings documented
- ✅ EDR alert tuning completed; alert volume normalized

### Q3 (270 days)
- ✅ CloudTrail centralized to Splunk; alerting rules active
- ✅ Database audit logging enabled for 90% of customer data access
- ✅ PAM platform pilot running; 30+ days of audit logs
- ✅ Quarterly backup restoration test completed

### Q4 (360 days)
- ✅ All Phase 1–2 initiatives complete; Phase 3 85%+ complete
- ✅ NIST maturity re-assessment: 2.5+ of 5.0 across Functions
- ✅ Risk register updated; quarterly review cycle established
- ✅ Year 2 roadmap drafted and approved

---

## Board Reporting Cadence

- **Steering Committee:** Monthly (first Monday)
- **Audit Committee:** Quarterly (risk register, compliance posture)
- **Board Risk Committee:** Quarterly (top risks, remediation progress, escalations)
- **Full Board:** Annual (executive summary, lessons learned, Year 2 planning)

---

**Next: Executive Summary & Portfolio Completion**
