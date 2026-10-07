# Top 10 Risks

---

## RK-001: Incomplete MFA on Administrative Accounts

**Threat:** Phishing, credential spray, or password compromise targeting admin accounts  
**Impact:** Unauthorized administrative access to customer data, configuration changes, service disruption

| Metric | Score |
|--------|-------|
| Inherent Likelihood | 4 (High) |
| Inherent Impact | 5 (Severe) |
| Inherent Risk Score | 20 (Critical) |
| Current Controls | MFA on some accounts; optional for password-only access |
| Residual Likelihood | 1 (MFA enforcement eliminates credential-only attacks) |
| Residual Risk Score | 5 (Moderate) |

**NIST CSF Mapping:** GV.RM (Risk Management Program), PR.AA (Access Management)

**Residual Assessment:** With MFA enforcement, phishing attacks alone cannot compromise admin accounts; attacker would need to compromise both credential and MFA token. Password spray becomes ineffective. Residual likelihood drops from 4 to 1.

**Recommendation (Priority 1):** Enforce MFA on all administrative accounts within 30 days. Establish policy: no admin access without MFA.

---

## RK-002: Service Account Credentials in Configuration Files

**Threat:** Exposure of database connection strings, backup credentials, or API keys in source code or configuration files; lateral movement after initial compromise

**Impact:** Attackers gain database access without detection; can modify customer data, extract backups, or escalate privileges

| Metric | Score |
|--------|-------|
| Inherent Likelihood | 4 (High) |
| Inherent Impact | 4 (High) |
| Inherent Risk Score | 16 (Critical) |
| Current Controls | Credentials stored in configuration files; no centralized secrets management |
| Residual Likelihood | 2 (Secrets platform reduces exposure; still depends on implementation) |
| Residual Risk Score | 8 (High) |

**NIST CSF Mapping:** PR.AA (Access Management), PR.DS (Data Security)

**Residual Assessment:** Migration to a secrets management platform (AWS Secrets Manager, HashiCorp Vault) reduces exposure. Residual likelihood assumes proper secret rotation and access controls. Monitoring for unauthorized secret access remains critical.

**Recommendation (Priority 1):** Migrate all service account credentials to secrets management platform within 60 days. Implement secret rotation policy (90-day cycle).

---

## RK-003: Untested Backup Restoration Procedures

**Threat:** Backup system failure, ransomware encryption of backups, hardware failure; inability to restore after data loss

**Impact:** Permanent data loss; business continuity failure; regulatory non-compliance; potential insolvency

| Metric | Score |
|--------|-------|
| Inherent Likelihood | 3 (Moderate) |
| Inherent Impact | 5 (Severe) |
| Inherent Risk Score | 15 (Critical) |
| Current Controls | Veeam backup system; daily full + incremental; last full restoration test April 2025 |
| Residual Likelihood | 3 (Untested restoration doesn't reduce risk; testing required to validate RTO/RPO) |
| Residual Risk Score | 15 (Critical) |

**NIST CSF Mapping:** RC.RP (Recovery Planning & Processes), PR.IR (Infrastructure Resilience)

**Residual Assessment:** Backup systems provide no reduction in residual risk without proven restoration capability. Last documented test was 18 months ago; quarterly testing is required. Untested backups are a liability, not a protection.

**Recommendation (Priority 2):** Establish quarterly backup restoration testing schedule and documented runbook within 45 days. Execute first test immediately. Track RTO/RPO against business requirements.

---

## RK-004: Cloud Misconfiguration (S3 Bucket Exposure)

**Threat:** S3 bucket exposed to public internet due to overly permissive bucket policies or ACLs; customer data exposure

**Impact:** Customer PII and financial data exposure; regulatory breach notification; reputational damage

| Metric | Score |
|--------|-------|
| Inherent Likelihood | 3 (Moderate) |
| Inherent Impact | 4 (High) |
| Inherent Risk Score | 12 (High) |
| Current Controls | AWS IAM policies; S3 encryption at rest; no continuous compliance monitoring |
| Residual Likelihood | 2 (Regular AWS Config compliance checks reduce exposure; depends on execution) |
| Residual Risk Score | 8 (High) |

**NIST CSF Mapping:** PR.AA (Access Management), PR.IR (Infrastructure Resilience)

**Residual Assessment:** AWS Config compliance rules can monitor bucket policies and ACLs continuously. Residual likelihood assumes Config is enabled, evaluated, and actioned on (not just logged).

**Recommendation (Priority 2):** Enable AWS Config rules for S3 bucket compliance within 45 days. Establish automated remediation for non-compliant buckets. Monthly manual audit of IAM policies.

---

## RK-005: Incomplete AWS CloudTrail Centralization to SIEM

**Threat:** AWS API activity not logged to central SIEM; unauthorized AWS actions undetected (IAM changes, credential creation, data exfiltration)

**Impact:** Delayed incident detection; attacker persistence in AWS environment; inability to forensically investigate AWS-based attacks

| Metric | Score |
|--------|-------|
| Inherent Likelihood | 3 (Moderate) |
| Inherent Impact | 4 (High) |
| Inherent Risk Score | 12 (High) |
| Current Controls | CloudTrail logging enabled; CloudWatch monitoring partial; not forwarded to Splunk |
| Residual Likelihood | 2 (Centralization to SIEM enables alerting; depends on rule tuning) |
| Residual Risk Score | 8 (High) |

**NIST CSF Mapping:** DE.CM (Continuous Monitoring), GV.RM (Risk Management Program)

**Residual Assessment:** CloudTrail logs forwarded to Splunk with alerting rules reduce detection time from hours to minutes. Residual likelihood assumes rule-based alerting on high-risk API calls (IAM policy changes, credential creation, S3 public access grants).

**Recommendation (Priority 2):** Centralize CloudTrail logs to Splunk within 45 days. Implement alerting rules for high-risk API actions within 60 days.

---

## RK-006: Third-Party Vendor Risk (Salesforce, ADP, Payment Processor)

**Threat:** Compromise of third-party SaaS vendors; customer data exposure or business disruption

**Impact:** Customer data breach; operational disruption; regulatory penalties; reputational damage

| Metric | Score |
|--------|-------|
| Inherent Likelihood | 2 (Low) |
| Inherent Impact | 4 (High) |
| Inherent Risk Score | 8 (High) |
| Current Controls | Informal vendor risk review; no formal risk assessment process |
| Residual Likelihood | 2 (Formal assessment doesn't reduce vendor's risk; improves HarborPoint's detection/response) |
| Residual Risk Score | 8 (High) |

**NIST CSF Mapping:** GV.SC (Supply Chain Risk Management), PR.DS (Data Security)

**Residual Assessment:** Formal third-party risk assessment improves HarborPoint's ability to detect and respond, but does not reduce vendor breach likelihood. Residual score remains high; mitigation focuses on detection (API monitoring, access controls, incident response with vendors).

**Recommendation (Priority 3):** Develop third-party risk assessment template and evaluate Salesforce, ADP, payment processor within 90 days. Establish vendor breach notification agreement and incident response procedures.

---

## RK-007: Ransomware Attack on Portal & Databases

**Threat:** Ransomware deployed via compromised endpoint, vulnerable web application, or third-party integration; encryption of portal, databases, and backups

**Impact:** Complete business disruption; payment processing halt; customer service disruption; revenue loss; regulatory penalties

| Metric | Score |
|--------|-------|
| Inherent Likelihood | 3 (Moderate) |
| Inherent Impact | 5 (Severe) |
| Inherent Risk Score | 15 (Critical) |
| Current Controls | EDR (CrowdStrike), WAF, network segmentation, backup strategy |
| Residual Likelihood | 2 (EDR detects and contains ransomware; assumes rapid response) |
| Residual Risk Score | 10 (High) |

**NIST CSF Mapping:** PR.AA (Access Management), DE.AE (Detection & Analysis), PR.IR (Infrastructure Resilience)

**Residual Assessment:** CrowdStrike Falcon detects ransomware behavioral signatures and contains execution. Residual likelihood assumes 1) CrowdStrike alerts are monitored, 2) incident response activates within 30 minutes, 3) backup separation and testing prevent total data loss.

**Recommendation (Priority 1–2):** Implement EDR tuning and alert escalation (30 days); execute ransomware tabletop exercise (45 days); test backup restoration under ransomware scenario (90 days).

---

## RK-008: Inadequate Incident Response Testing

**Threat:** Security incident occurs; incident response plan fails due to untested procedures, unclear roles, or tool failures

**Impact:** Delayed incident containment; extended breach duration; regulatory non-compliance; reputational damage

| Metric | Score |
|--------|-------|
| Inherent Likelihood | 2 (Low) |
| Inherent Impact | 4 (High) |
| Inherent Risk Score | 8 (High) |
| Current Controls | Incident response plan exists; no documented testing or drills |
| Residual Likelihood | 2 (Testing improves readiness; does not reduce incident probability) |
| Residual Risk Score | 8 (High) |

**NIST CSF Mapping:** PR.IR (Infrastructure Resilience), ID.RA (Risk Assessment)

**Residual Assessment:** Incident response plans are hypothetical until tested. Tabletop exercises and simulations reveal gaps in procedures, tool integration, and role clarity. Residual likelihood remains stable; mitigation reduces time-to-containment.

**Recommendation (Priority 3):** Conduct ransomware tabletop exercise (60 days); document lessons learned; update IR plan (90 days); execute credential compromise simulation (6 months).

---

## RK-009: Multi-Region Failover Gap

**Threat:** AWS region failure or unavailability; portal application becomes unavailable; business continuity failure

**Impact:** Customer access blocked; payment processing halted; revenue loss during recovery; regulatory non-compliance

| Metric | Score |
|--------|-------|
| Inherent Likelihood | 1 (Unlikely) |
| Inherent Impact | 5 (Severe) |
| Inherent Risk Score | 5 (Moderate) |
| Current Controls | Single-region deployment; no documented failover; backup strategy exists |
| Residual Likelihood | 1 (Multi-region failover would reduce, but does not exist; current state unchanged) |
| Residual Risk Score | 5 (Moderate) |

**NIST CSF Mapping:** RC.RP (Recovery Planning), PR.IR (Infrastructure Resilience)

**Residual Assessment:** This risk is primarily a gap (multi-region failover not implemented). Residual likelihood remains 1 (AWS regional outage is rare, ~99.9% availability SLA). Business impact is high; mitigation is architectural (expensive). RTO tolerance (2 hours for portal) must drive investment decision.

**Recommendation (Priority 4—Lower Priority for 175-person bank):** Evaluate multi-region DR/failover strategy; estimated cost $100K–$150K + ongoing; assess business case. If not pursued, document risk acceptance and establish alternate recovery procedures (manual failover, data restoration).

---

## RK-010: Privilege Access Management (PAM) Gap

**Threat:** Elevated privileges not actively managed; privileged accounts accessed without audit; lateral movement after compromise

**Impact:** Unauthorized access to sensitive systems; data modification; regulatory non-compliance

| Metric | Score |
|--------|-------|
| Inherent Likelihood | 2 (Low) |
| Inherent Impact | 4 (High) |
| Inherent Risk Score | 8 (High) |
| Current Controls | MFA on some accounts; manual privilege management; no PAM platform |
| Residual Likelihood | 2 (PAM platform improves logging/isolation; requires implementation rigor) |
| Residual Risk Score | 8 (High) |

**NIST CSF Mapping:** ID.AM (Asset Management), GV.OV (Oversight)

**Residual Assessment:** PAM platform (e.g., CyberArk, Delinea) centralizes privileged credential management and session recording. Residual likelihood assumes implementation of least-privilege access, just-in-time (JIT) provisioning, and audit logging.

**Recommendation (Priority 3):** Evaluate PAM platform options (60 days); implement JIT access workflow for database and admin accounts (6 months); estimated cost $50K–$75K + implementation.

---

## Summary: Top 10 by Residual Risk Score

| Rank | Risk | Residual Score | Priority |
|------|------|-----------------|----------|
| 1 | Incomplete MFA on Admin Accounts | 5 (Moderate) | 1 |
| 2 | Untested Backup Restoration | 15 (Critical) | 2 |
| 3 | Service Account Credentials in Files | 8 (High) | 1 |
| 4 | Cloud Misconfiguration | 8 (High) | 2 |
| 5 | CloudTrail Centralization Gap | 8 (High) | 2 |
| 6 | Third-Party Vendor Risk | 8 (High) | 3 |
| 7 | Ransomware Attack | 10 (High) | 1–2 |
| 8 | Incident Response Testing Gap | 8 (High) | 3 |
| 9 | Multi-Region Failover Gap | 5 (Moderate) | 4 |
| 10 | PAM Gap | 8 (High) | 3 |

**Critical Residual Risks:** RK-003 (Untested Backup) remains Critical even after control assessment because untested procedures provide no actual protection.

**Priority 1 (Next 30–60 days):** RK-001, RK-002, RK-007  
**Priority 2 (Next 45–90 days):** RK-003, RK-004, RK-005  
**Priority 3–4:** RK-006, RK-008, RK-009, RK-010

---

**Next: NIST CSF 2.0 Maturity Assessment & Gap Analysis**
