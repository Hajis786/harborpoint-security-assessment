# HarborPoint Financial Services — Scenario & Assessment Scope

## Company Scenario

HarborPoint is a regional bank headquartered in Maryland, serving the Mid-Atlantic with three branch locations (Maryland, Virginia, Pennsylvania). The organization provides wealth management, small business lending, investment advisory, and deposit accounts to roughly 40,000 customers.

**Size:** 175 employees; $35M annual revenue; ~8–10% operating margin

**Business Model:**
- Wealth management and advisory: 30%
- Small business lending: 40%
- Deposits and banking: 20%
- Investment products: 10%

**Customer base:** Geographically concentrated; no single customer exceeds 3% of revenue. Differentiated through personalized service and fast lending decisions rather than technological innovation.

---

## Technology Environment

**Identity & Access:**
- Microsoft Entra ID for employee identity
- Incomplete MFA enforcement; some admin roles allow password-only access
- Service account credentials stored in configuration files (no secrets management platform)
- No privileged access management system

**Endpoints:**
- 160 Windows 11 devices
- CrowdStrike Falcon EDR active
- Intune for mobile device and endpoint management
- Windows Defender antivirus

**Cloud Infrastructure:**
- Single AWS region (no multi-region failover)
- EC2 for customer portal application (load-balanced)
- RDS PostgreSQL read-only replica for analytics
- S3 for backup storage and document archive
- CloudTrail logging enabled; CloudWatch monitoring partial

**On-Premises:**
- PostgreSQL primary database (writable, customer data)
- Veeam backup system (daily full, incremental every 4 hours)
- Fortinet FortiGate firewall at HQ
- Consumer-grade firewalls at branches

**Applications:**
- Microsoft 365 (email, collaboration, calendar)
- Salesforce CRM (lending pipeline, customer management)
- QuickBooks Online (accounting)
- GitHub private repositories (source code)

**Monitoring & Logging:**
- Splunk Enterprise (~60–70% system coverage)
- AWS WAF for web application protection
- Rapid7 Nexpose for quarterly vulnerability scans

**Network:**
- Dual ISP with automatic failover at HQ
- Single ISP per branch location (Virginia, Pennsylvania)
- Meraki SD-WAN deployed at 2 of 3 locations
- AWS Client VPN for remote employees (~40 staff)

---

## Assessment Scope

**Objectives:**
1. Identify and prioritize cybersecurity risks to business-critical processes
2. Assess current maturity against NIST CSF 2.0 Subcategories
3. Define target maturity state and gap analysis
4. Develop phased remediation roadmap with business justification

**Assessment Period:** October 2026 (1 month, simulated)

**In Scope:**
- Cloud infrastructure (AWS) and on-premises systems
- Identity and access management
- Backup and disaster recovery
- Data protection and database security
- Vendor and third-party risk
- Monitoring and incident response capabilities

**Out of Scope:**
- Detailed penetration testing or vulnerability assessment
- Compliance audit (FDIC, GLBA, BSA/AML)
- Detailed code review or application security testing
- Forensic analysis of past incidents
- Physical security assessment

---

## Critical Business Processes

| Process | RTO | RPO | Impact if Unavailable |
|---------|-----|-----|----------------------|
| Customer onboarding (KYC/AML) | 4 hours | 1 hour | Regulatory non-compliance; revenue loss |
| Loan origination & underwriting | 4 hours | 1 hour | Loss of core revenue source |
| Customer portal (login, transfers, payments) | 2 hours | 15 min | Customer frustration; cash flow impact |
| Payment processing | 2 hours | 15 min | Lost transactions; customer dissatisfaction |
| Financial reporting & compliance | 8 hours | 1 day | Regulatory reporting delays |
| Incident response & investigation | Immediate | N/A | Breach containment, remediation |

---

## Regulatory & Compliance Context

HarborPoint is subject to:
- **FDIC regulation and examination** (safety and soundness)
- **State banking regulation** (consumer compliance)
- **GLBA** (Gramm-Leach-Bliley Act) — data protection and safeguards
- **FFIEC guidance** — IT security and operational resilience
- **Basel III** — operational risk management

Breach notification obligations depend on the nature of the incident, affected information, and applicable jurisdiction and regulatory status.

---

## Threat Landscape

**Ransomware:** Financial services is a high-value target. Ransomware attacks halt customer transactions and loan processing. Likelihood: High. Impact: Severe (revenue loss, regulatory penalties, reputational damage).

**Credential compromise:** Phishing, password spray, and brute-force attacks are common in financial services. Compromised credentials enable unauthorized access to customer data and unauthorized transactions. Likelihood: High. Impact: High (customer data exposure, regulatory reporting).

**Cloud misconfiguration:** S3 bucket exposure, overly permissive IAM policies, incomplete logging. Common in organizations with rapid cloud adoption. Impact: High (data exposure). Likelihood: Moderate.

**Third-party breach:** Compromise of Salesforce, ADP, or payment processors would affect customer data or operations. Likelihood: Moderate. Impact: Depends on vendor.

**Backup failure:** Untested restoration procedures, ransomware encryption of backups, or hardware failure. Likelihood: Moderate (testing overdue since April 2025). Impact: High (data loss, business continuity failure).

---

## Assessment Methodology (Detailed)

### Risk Scoring

Risks are scored using a 5×5 Likelihood × Impact matrix:

**Likelihood** (1–5):
- 1 = Unlikely (attack requires significant effort or exploit rarity)
- 2 = Low (occasional occurrence)
- 3 = Moderate (plausible exploitation)
- 4 = High (common attack vector in financial services)
- 5 = Almost Certain (active exploitation; control gaps significant)

**Impact** (1–5):
- 1 = Minimal (limited data, brief downtime)
- 2 = Low (some customer/operational impact)
- 3 = Moderate (significant operational impact; customer data exposure)
- 4 = High (severe disruption; large-scale data exposure; regulatory penalties)
- 5 = Severe (complete business disruption; existential threat)

**Risk Rating:** Likelihood × Impact (1–25)
- Critical: 16–25
- High: 8–15
- Moderate: 4–7
- Low: 1–3

### Residual Risk

Residual likelihood is adjusted after considering the effectiveness of existing controls. For example:

- **Phishing risk (Likelihood 4 baseline):** With MFA enforcement, residual likelihood drops to 1 (MFA defeats credential-only attacks)
- **Backup failure (Likelihood 4 baseline):** Without tested restoration procedures, residual likelihood remains 4

Residual likelihood is determined through documented judgment, not percentage formulas.

### NIST CSF 2.0 Maturity Assessment

Current state is assessed against 22 NIST CSF 2.0 Subcategories across six Functions. Maturity is rated on a 0–5 scale:

- 0 = Not Implemented
- 1 = Initial (ad-hoc)
- 2 = Developing (documented, limited consistency)
- 3 = Defined (standardized, repeatable)
- 4 = Managed (metrics-driven)
- 5 = Optimized (proactive, integrated)

This project-specific maturity scale is separate from NIST CSF 2.0 outcome assessment.

---

**Next:** Assessment findings and top risks
