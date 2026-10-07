# Top 10 Risks

---

## RK-001: Incomplete MFA on Administrative Accounts

**Threat:** Phishing, credential spray, or password compromise targeting admin accounts  
**Impact:** Unauthorized administrative access to customer data, configuration changes, service disruption

| Metric | Score |
|--------|-------|
| **Inherent Risk (No Controls)** | |
| Inherent Likelihood | 4 (High) |
| Inherent Impact | 5 (Severe) |
| Inherent Risk Score | 20 (Critical) |
| **Current Residual Risk (Existing Controls Only)** | |
| Current Controls | MFA on some accounts; optional for password-only access |
| Current Residual Likelihood | 3 (MFA partial; many accounts lack MFA) |
| Current Residual Risk Score | 15 (Critical) |
| **Target Risk (After Recommendation)** | |
| Recommended Control | Enforce MFA on all administrative accounts (30 days) |
| Target Residual Likelihood | 1 (MFA enforcement eliminates credential-only attacks) |
| Target Residual Risk Score | 5 (Moderate) |

**NIST CSF Mapping:** GV.RM (Risk Management Strategy), PR.AA (Access Management)

**Current Residual Assessment:** Partial MFA deployment leaves admin accounts vulnerable. Phishing and credential spray remain viable attack vectors for non-MFA accounts.

**Target Assessment:** Full MFA enforcement means phishing alone cannot compromise admin accounts; attacker must compromise both credential and MFA token. Password spray becomes ineffective.

**Recommendation (Priority 1):** Enforce MFA on all administrative accounts within 30 days. Establish policy: no admin access without MFA.

---

## RK-002: Service Account Credentials in Configuration Files

**Threat:** Exposure of database connection strings, backup credentials, or API keys in source code or configuration files; lateral movement after initial compromise

**Impact:** Attackers gain database access without detection; can modify customer data, extract backups, or escalate privileges

| Metric | Score |
|--------|-------|
| **Inherent Risk (No Controls)** | |
| Inherent Likelihood | 4 (High) |
| Inherent Impact | 4 (High) |
| Inherent Risk Score | 16 (Critical) |
| **Current Residual Risk (Existing Controls Only)** | |
| Current Controls | Credentials stored in configuration files; no centralized secrets management |
| Current Residual Likelihood | 4 (No change; credentials remain exposed in files) |
| Current Residual Risk Score | 16 (Critical) |
| **Target Risk (After Recommendation)** | |
| Recommended Control | Migrate to secrets management platform (60 days); 90-day rotation |
| Target Residual Likelihood | 2 (Centralized secrets platform reduces exposure risk) |
| Target Residual Risk Score | 8 (High) |

**NIST CSF Mapping:** PR.AA (Access Management), PR.DS (Data Security)

**Current Residual Assessment:** Service account credentials remain exposed in configuration files. No centralized access control or rotation mechanism. Compromise of any code repository or configuration file yields database access.

**Target Assessment:** Migration to AWS Secrets Manager or equivalent centralizes credential management, enables automated rotation, and provides audit logging. Access must be controlled via IAM policies.

**Recommendation (Priority 1):** Migrate all service account credentials to secrets management platform within 60 days. Implement secret rotation policy (90-day cycle).

---

## RK-003: Untested Backup Restoration Procedures

**Threat:** Backup system failure, ransomware encryption of backups, hardware failure; inability to restore after data loss

**Impact:** Permanent data loss; business continuity failure; regulatory non-compliance; potential insolvency

| Metric | Score |
|--------|-------|
| **Inherent Risk (No Controls)** | |
| Inherent Likelihood | 3 (Moderate) |
| Inherent Impact | 5 (Severe) |
| Inherent Risk Score | 15 (Critical) |
| **Current Residual Risk (Existing Controls Only)** | |
| Current Controls | Veeam backup system; daily full + incremental; last test April 2025 (18 months ago) |
| Current Residual Likelihood | 3 (Backup exists but untested; no proven recovery capability) |
| Current Residual Risk Score | 15 (Critical) |
| **Target Risk (After Recommendation)** | |
| Recommended Control | Establish quarterly restoration testing; validate RTO/RPO; document runbook |
| Target Residual Likelihood | 2 (Quarterly testing validates recovery capability; residual risk decreases with proof) |
| Target Residual Risk Score | 10 (High) |

**NIST CSF Mapping:** RC.RP (Recovery Planning), PR.IR (Infrastructure Resilience)

**Current Residual Assessment:** Backup systems exist but have not been validated. Last documented full restoration test was 18 months ago. Untested backups provide false assurance; actual recovery capability is unknown.

**Target Assessment:** Quarterly restoration testing with documented runbook and validated RTO/RPO targets reduces residual risk. Testing must occur before backup system failure.

**Recommendation (Priority 1–2):** Establish quarterly backup restoration testing schedule and documented runbook within 45 days. Execute first test immediately. Track RTO/RPO against business requirements.

---

## RK-004: Cloud Misconfiguration (S3 Bucket Exposure)

**Threat:** S3 bucket exposed to public internet due to overly permissive bucket policies or ACLs; customer data exposure

**Impact:** Customer PII and financial data exposure; regulatory breach notification; reputational damage

| Metric | Score |
|--------|-------|
| **Inherent Risk (No Controls)** | |
| Inherent Likelihood | 3 (Moderate) |
| Inherent Impact | 4 (High) |
| Inherent Risk Score | 12 (High) |
| **Current Residual Risk (Existing Controls Only)** | |
| Current Controls | AWS IAM policies; S3 encryption at rest; no continuous compliance monitoring |
| Current Residual Likelihood | 3 (Manual IAM policies only; no automated detection of misconfiguration) |
| Current Residual Risk Score | 12 (High) |
| **Target Risk (After Recommendation)** | |
| Recommended Control | AWS Config compliance rules; automated remediation; monthly manual audit |
| Target Residual Likelihood | 2 (Continuous compliance monitoring reduces exposure window) |
| Target Residual Risk Score | 8 (High) |

**NIST CSF Mapping:** PR.AA (Access Management), PR.DS (Data Security)

**Current Residual Assessment:** AWS IAM policies and S3 encryption provide baseline controls but no real-time detection of misconfiguration. Changes to bucket policies are not automatically monitored or alerted.

**Target Assessment:** AWS Config enables continuous compliance monitoring. Misconfigurations are detected within minutes and can be remediated automatically or manually reviewed before exposure.

**Recommendation (Priority 2):** Enable AWS Config rules for S3 bucket compliance within 45 days. Establish automated remediation for non-compliant buckets. Monthly manual audit of IAM policies.

---

## RK-005: Incomplete AWS CloudTrail Centralization to SIEM

**Threat:** AWS API activity not logged to central SIEM; unauthorized AWS actions undetected (IAM changes, credential creation, data exfiltration)

**Impact:** Delayed incident detection; attacker persistence in AWS environment; inability to forensically investigate AWS-based attacks

| Metric | Score |
|--------|-------|
| **Inherent Risk (No Controls)** | |
| Inherent Likelihood | 3 (Moderate) |
| Inherent Impact | 4 (High) |
| Inherent Risk Score | 12 (High) |
| **Current Residual Risk (Existing Controls Only)** | |
| Current Controls | CloudTrail logging enabled; CloudWatch monitoring partial; not forwarded to Splunk |
| Current Residual Likelihood | 3 (CloudTrail logs captured but not centralized; detection relies on manual review) |
| Current Residual Risk Score | 12 (High) |
| **Target Risk (After Recommendation)** | |
| Recommended Control | Centralize CloudTrail to Splunk (45 days); implement alerting on high-risk API calls (60 days) |
| Target Residual Likelihood | 2 (Automated SIEM alerting reduces detection time from hours to minutes) |
| Target Residual Risk Score | 8 (High) |

**NIST CSF Mapping:** DE.CM (Continuous Monitoring), GV.RM (Risk Management Strategy)

**Current Residual Assessment:** CloudTrail logs exist but are not centralized to SIEM. Investigation of AWS-based attacks requires manual log review. Detection latency is hours to days.

**Target Assessment:** Centralization to Splunk with rule-based alerting enables near-real-time detection. Alerting rules cover high-risk actions (IAM policy changes, credential creation, S3 public access grants).

**Recommendation (Priority 2):** Centralize CloudTrail logs to Splunk within 45 days. Implement alerting rules for high-risk API actions within 60 days.

---

## RK-006: Third-Party Vendor Risk (Salesforce, ADP, Payment Processor)

**Threat:** Compromise of third-party SaaS vendors; customer data exposure or business disruption

**Impact:** Customer data breach; operational disruption; regulatory penalties; reputational damage

| Metric | Score |
|--------|-------|
| **Inherent Risk (No Controls)** | |
| Inherent Likelihood | 2 (Low) |
| Inherent Impact | 4 (High) |
| Inherent Risk Score | 8 (High) |
| **Current Residual Risk (Existing Controls Only)** | |
| Current Controls | Informal vendor risk review; no formal risk assessment process; no SLAs or incident response agreements |
| Current Residual Likelihood | 2 (Vendor likelihood unchanged; HarborPoint has no detection mechanism) |
| Current Residual Risk Score | 8 (High) |
| **Target Risk (After Recommendation)** | |
| Recommended Control | Formal vendor risk assessment template; SLAs; incident response agreements with vendors |
| Target Residual Likelihood | 2 (Formal assessment improves detection/response but does not reduce vendor breach likelihood) |
| Target Residual Risk Score | 8 (High) |

**NIST CSF Mapping:** GV.SC (Supply Chain Risk Management), PR.DS (Data Security)

**Current Residual Assessment:** Vendor risk is managed informally. No documented assessment of vendor security posture, no SLAs, no incident response agreements. HarborPoint has limited visibility into vendor breach notifications.

**Target Assessment:** Formal vendor risk assessment process improves detection and incident response but does not reduce the likelihood of vendor compromise. Residual score remains high as vendor breach is external to HarborPoint's control.

**Recommendation (Priority 3):** Develop third-party risk assessment template and evaluate Salesforce, ADP, payment processor within 90 days. Establish vendor breach notification agreement and incident response procedures.

---

## RK-007: Ransomware Attack on Portal & Databases

**Threat:** Ransomware deployed via compromised endpoint, vulnerable web application, or third-party integration; encryption of portal, databases, and backups

**Impact:** Complete business disruption; payment processing halt; customer service disruption; revenue loss; regulatory penalties

| Metric | Score |
|--------|-------|
| **Inherent Risk (No Controls)** | |
| Inherent Likelihood | 3 (Moderate) |
| Inherent Impact | 5 (Severe) |
| Inherent Risk Score | 15 (Critical) |
| **Current Residual Risk (Existing Controls Only)** | |
| Current Controls | EDR (CrowdStrike), WAF, network segmentation, backup strategy; EDR alerting not tuned; IR plan untested |
| Current Residual Likelihood | 3 (EDR exists but alerts not optimized; IR plan untested; response time unknown) |
| Current Residual Risk Score | 15 (Critical) |
| **Target Risk (After Recommendation)** | |
| Recommended Control | EDR alert tuning (30 days); IR playbook (45 days); backup restoration testing (90 days) |
| Target Residual Likelihood | 2 (EDR detects and contains; 30-minute response SLA; backup separation validated) |
| Target Residual Risk Score | 10 (High) |

**NIST CSF Mapping:** PR.AA (Access Management), DE.AE (Detection & Analysis), PR.IR (Infrastructure Resilience)

**Current Residual Assessment:** Ransomware defenses exist but are not optimized. EDR is deployed but alert tuning is incomplete. Incident response plan is untested; actual response capability is unknown. Backup strategy exists but has not been validated under ransomware scenario.

**Target Assessment:** EDR alert tuning enables detection and containment within minutes. Tested IR playbook ensures 30-minute escalation. Quarterly backup restoration testing validates recovery under ransomware conditions.

**Recommendation (Priority 1–2):** Implement EDR tuning and alert escalation (30 days); execute ransomware tabletop exercise (45 days); test backup restoration under ransomware scenario (90 days).

---

## RK-008: Inadequate Incident Response Testing

**Threat:** Security incident occurs; incident response plan fails due to untested procedures, unclear roles, or tool failures

**Impact:** Delayed incident containment; extended breach duration; regulatory non-compliance; reputational damage

| Metric | Score |
|--------|-------|
| **Inherent Risk (No Controls)** | |
| Inherent Likelihood | 2 (Low) |
| Inherent Impact | 4 (High) |
| Inherent Risk Score | 8 (High) |
| **Current Residual Risk (Existing Controls Only)** | |
| Current Controls | Incident response plan exists; no documented testing, drills, or role clarity |
| Current Residual Likelihood | 2 (Plan exists but untested; actual capability unknown) |
| Current Residual Risk Score | 8 (High) |
| **Target Risk (After Recommendation)** | |
| Recommended Control | Tabletop exercise (60 days); incident playbooks (documented roles, escalation, timelines); quarterly drills |
| Target Residual Likelihood | 2 (Testing improves readiness; does not reduce incident likelihood) |
| Target Residual Risk Score | 8 (High) |

**NIST CSF Mapping:** RS.MA (Response Mobilization), RS.MI (Response Mitigation)

**Current Residual Assessment:** IR plan is written but has never been tested. Roles are not clearly defined. Tool integration is untested. Actual response capability is unknown.

**Target Assessment:** Tabletop exercises and simulations reveal gaps in procedures, tool integration, and role clarity. Regular testing ensures procedures remain current and staff remain trained. Residual likelihood remains stable; mitigation is improved time-to-containment and reduced recovery time.

**Recommendation (Priority 2):** Conduct ransomware tabletop exercise (60 days); document lessons learned; establish annual IR drill schedule; execute credential compromise simulation (6 months).

---

## RK-009: Multi-Region Failover Gap

**Threat:** AWS region failure or unavailability; portal application becomes unavailable; business continuity failure

**Impact:** Customer access blocked; payment processing halted; revenue loss during recovery; regulatory non-compliance

| Metric | Score |
|--------|-------|
| **Inherent Risk (No Controls)** | |
| Inherent Likelihood | 1 (Unlikely) |
| Inherent Impact | 5 (Severe) |
| Inherent Risk Score | 5 (Moderate) |
| **Current Residual Risk (Existing Controls Only)** | |
| Current Controls | Single-region deployment; no documented failover; backup strategy exists |
| Current Residual Likelihood | 1 (AWS regional outage is rare; single-region deployment is the only gap) |
| Current Residual Risk Score | 5 (Moderate) |
| **Target Risk (After Recommendation)** | |
| Recommended Control | Multi-region failover architecture (business case assessment; 6+ months implementation) |
| Target Residual Likelihood | 1 (Multi-region failover reduces RTO; likelihood remains low due to AWS SLA) |
| Target Residual Risk Score | 5 (Moderate) |

**NIST CSF Mapping:** RC.RP (Recovery Planning), PR.IR (Infrastructure Resilience)

**Current Residual Assessment:** Single-region deployment means portal unavailability during regional outages. Backup strategy supports data recovery but not failover. AWS regional outages are rare (~99.9% SLA) but impact is high.

**Target Assessment:** Multi-region failover reduces RTO to minutes. Likelihood remains low due to AWS redundancy. Investment is architectural and expensive ($$$+).

**Recommendation (Priority 4—Lower Priority for 175-person bank):** Evaluate multi-region DR/failover strategy as business case (estimated cost $$$ range + ongoing operations); assess against RTO/RPO targets. If not pursued, document risk acceptance and establish alternate recovery procedures (manual failover, data restoration from backups).

---

## RK-010: Privilege Access Management (PAM) Gap

**Threat:** Elevated privileges not actively managed; privileged accounts accessed without audit; lateral movement after compromise

**Impact:** Unauthorized access to sensitive systems; data modification; regulatory non-compliance

| Metric | Score |
|--------|-------|
| **Inherent Risk (No Controls)** | |
| Inherent Likelihood | 2 (Low) |
| Inherent Impact | 4 (High) |
| Inherent Risk Score | 8 (High) |
| **Current Residual Risk (Existing Controls Only)** | |
| Current Controls | MFA on some accounts; manual privilege management; no PAM platform; no session recording |
| Current Residual Likelihood | 2 (Partial MFA; no centralized audit of privileged access) |
| Current Residual Risk Score | 8 (High) |
| **Target Risk (After Recommendation)** | |
| Recommended Control | PAM platform implementation (CyberArk/Delinea); JIT access; session recording; least-privilege policies |
| Target Residual Likelihood | 2 (PAM improves audit and isolation but does not eliminate insider risk) |
| Target Residual Risk Score | 8 (High) |

**NIST CSF Mapping:** ID.AM (Asset Management), PR.AA (Access Management)

**Current Residual Assessment:** Privileges are managed manually without centralized audit or session recording. Privileged account access is not tracked. Insider threat risk is unmitigated.

**Target Assessment:** PAM platform centralizes credential management, enforces least-privilege access, and records privileged sessions. Just-in-time (JIT) provisioning reduces standing privilege exposure. Residual likelihood remains stable; insider threat is inherent.

**Recommendation (Priority 3):** Evaluate PAM platform options (60 days); implement JIT access workflow for database and admin accounts (6+ months); plan for $$ investment range.

---

## Summary: Top 10 by Current Residual Risk Score

| Rank | Risk | Current Residual Score | Target Score | Priority |
|------|------|------------------------|---------------|----------|
| 1 | Untested Backup Restoration | 15 (Critical) | 10 (High) | 1–2 |
| 2 | Ransomware Attack | 15 (Critical) | 10 (High) | 1–2 |
| 3 | Incomplete MFA on Admin Accounts | 15 (Critical) | 5 (Moderate) | 1 |
| 4 | Service Account Credentials in Files | 16 (Critical) | 8 (High) | 1 |
| 5 | Cloud Misconfiguration | 12 (High) | 8 (High) | 2 |
| 6 | CloudTrail Centralization Gap | 12 (High) | 8 (High) | 2 |
| 7 | Third-Party Vendor Risk | 8 (High) | 8 (High) | 3 |
| 8 | Incident Response Testing Gap | 8 (High) | 8 (High) | 2 |
| 9 | PAM Gap | 8 (High) | 8 (High) | 3 |
| 10 | Multi-Region Failover Gap | 5 (Moderate) | 5 (Moderate) | 4 |

**Critical Current Residual Risks (16–20):** RK-002 (Service Accounts)  
**Critical Current Residual Risks (15):** RK-003 (Backup), RK-007 (Ransomware), RK-001 (MFA)  

**Priority 1 (Next 30–60 days):** RK-001 (MFA), RK-002 (Service Accounts), RK-007 (Ransomware)  
**Priority 2 (Next 45–90 days):** RK-003 (Backup), RK-004 (S3), RK-005 (CloudTrail), RK-008 (IR Testing)  
**Priority 3:** RK-006 (Vendor), RK-010 (PAM)  
**Priority 4:** RK-009 (Multi-Region)

---

**Next: NIST CSF 2.0 Maturity Assessment & Gap Analysis**
