# HarborPoint Financial Services — Security Assessment Portfolio
## Complete Public Version (18–22 Pages)

**Assessment Date:** October 2026  
**Assessment Framework:** NIST Cybersecurity Framework 2.0  
**Portfolio Purpose:** Demonstrate enterprise security risk assessment, control gap analysis, and remediation roadmap development  
**Audience:** Security practitioners, compliance/GRC professionals, hiring managers, enterprise architects

---

## Portfolio Contents

### 1. README & Navigation
- **`PUBLIC_README.md`** (Full Overview)
  - Project context and learning objectives
  - Assessment methodology (risk scoring, maturity model, NIST CSF 2.0 application)
  - Key findings summary
  - Repository structure and how to navigate the assessment
  - What was demonstrated and what was learned

### 2. Foundation & Context
- **`PUBLIC_01_Disclaimer.md`** (Simulation Scope)
  - Portfolio is a complete simulation; no real organization involved
  - Assessment scope and what was/was not included
  - Limitations of the assessment
  - Intended use case and audience

- **`PUBLIC_02_Company_Scenario.md`** (Business Context)
  - Company profile: 175-person regional bank, $35M revenue, 40,000 customers
  - Technology environment: cloud infrastructure, identity systems, endpoints, applications, monitoring
  - Business processes and RTO/RPO targets
  - Regulatory context (FDIC, GLBA, FFIEC, Basel III)
  - Threat landscape relevant to financial services
  - Assessment methodology (risk scoring framework, NIST maturity scale, residual risk assessment)

### 3. Architecture & Infrastructure
- **`PUBLIC_03_Architecture.md`** (System Design & Security Controls)
  - Logical architecture (three domains: external, enterprise, data)
  - Text-based architecture diagram showing all systems and data flows
  - Critical data flows: customer portal, employee access, backup/recovery, monitoring
  - Single points of failure and mitigation strategies
  - Network segmentation (HQ, branches, AWS cloud)
  - Identity architecture (workforce Entra ID vs. customer portal authentication)
  - Identified architecture gaps and security risks

### 4. Risk Analysis
- **`PUBLIC_04_Top_10_Risks.md`** (Detailed Risk Register)
  - 10 critical and high risks prioritized by residual score
  - Each risk includes:
    * Threat description and business impact
    * Inherent likelihood and impact scoring (5×5 matrix)
    * Current controls and residual likelihood assessment
    * NIST CSF 2.0 mappings (official identifiers only)
    * Remediation recommendations with priority and timeline
  - Risk summary table (ranked by residual score)
  - Risk categorization by priority (P1–P4 over 12 months)

- **`PUBLIC_05_NIST_Gap_Analysis.md`** (Maturity Assessment)
  - Current organizational maturity: 1.8 of 5.0 (Initial/Developing)
  - Target maturity: 2.8 of 5.0 (Defined) by end of Year 1
  - Detailed assessment of all 6 NIST CSF 2.0 Functions:
    * Govern (GV): Risk management, supply chain, oversight, policy
    * Identify (ID): Asset management, risk assessment
    * Protect (PR): Access control, data security, infrastructure resilience, platform security, awareness/training
    * Detect (DE): Continuous monitoring, detection & analysis
    * Respond (RS): Response mobilization, response mitigation
    * Recover (RC): Recovery planning
  - Current vs. target maturity by Function with gap analysis
  - Investment and timeline ($475K Year 1)

### 5. Remediation Strategy
- **`PUBLIC_06_Remediation_Roadmap.md`** (12-Month Execution Plan)
  - 4-phase phased approach (Q1–Q4 2027):
    * Phase 1 (Months 1–3, $115K): Immediate actions (MFA, backup testing, governance, incident response)
    * Phase 2 (Months 4–6, $145K): Control implementation (AWS Config, CloudTrail, audit logging, PAM eval)
    * Phase 3 (Months 7–9, $145K): Enhancement & testing (PAM impl., JIT access, threat hunting, testing)
    * Phase 4 (Months 10–12, $70K): Optimization & documentation (metrics, compliance verify, Year 2 planning)
  - Detailed initiative table per phase with owner, timeline, cost, residual risk impact
  - Dependencies and risk mitigation for each phase
  - Resource requirements and staffing plan
  - Success metrics by quarter
  - Risk of not executing

- **`PUBLIC_07_Executive_Dashboard.md`** (Progress Tracking)
  - Maturity overview and current status
  - Top 10 risks table with remediation timeline
  - Phase progress checklist and key milestones
  - Resource allocation and staffing plan
  - Critical success factors
  - Risk acceptance and board reporting framework
  - Quarterly success metrics

### 6. Executive Communication
- **`PUBLIC_08_Executive_Summary.md`** (Board-Level Overview)
  - Assessment findings (current maturity 1.8/5.0, target 2.8/5.0)
  - Critical risks (RK-003 Backup, RK-007 Ransomware)
  - High-risk findings (7 risks requiring Phase 1–3 remediation)
  - NIST CSF 2.0 maturity by Function
  - Remediation investment ($475K) and phased timeline
  - Top 12 recommendations in priority sequence
  - Regulatory alignment (FDIC, GLBA, FFIEC)
  - Risk of not executing (scenarios)
  - Organizational readiness assessment
  - Board-level voting recommendations and expected outcomes
  - Discussion questions for Board approval

---

## Key Metrics at a Glance

| Metric | Value |
|--------|-------|
| **Assessment Period** | 1 month (simulated October 2026) |
| **Organization Size** | 175 employees; $35M revenue |
| **Customer Base** | 40,000 customers (40% wealth mgmt, 40% lending, 20% deposits) |
| **Current NIST Maturity** | 1.8 of 5.0 (Initial/Developing) |
| **Target NIST Maturity (Year 1)** | 2.8 of 5.0 (Defined) |
| **Top Risks Identified** | 10 (2 Critical residual; 7 High residual; 1 Moderate residual) |
| **Year 1 Investment** | ~$475K (tools, services, staffing) |
| **Staffing Plan** | Additional 0.5 FTE security engineer; reallocation of existing staff |
| **Phases** | 4 phases over 12 months (Q1–Q4 2027) |

---

## How to Use This Portfolio

### For Hiring Managers & Recruiters
- Start with **`PUBLIC_README.md`** for project overview and learnings
- Review **`PUBLIC_08_Executive_Summary.md`** for decision-making approach and board communication
- Skim **`PUBLIC_04_Top_10_Risks.md`** for risk prioritization methodology
- Note the **`PUBLIC_07_Executive_Dashboard.md`** for metrics and progress tracking concepts

### For Security Practitioners
- Read **`PUBLIC_02_Company_Scenario.md`** to understand the environment
- Study **`PUBLIC_03_Architecture.md`** for system design and data flow analysis
- Deep-dive **`PUBLIC_04_Top_10_Risks.md`** for risk assessment and NIST CSF mapping
- Review **`PUBLIC_05_NIST_Gap_Analysis.md`** for maturity assessment methodology
- Examine **`PUBLIC_06_Remediation_Roadmap.md`** for phased implementation planning

### For Compliance/GRC Professionals
- Review **`PUBLIC_01_Disclaimer.md`** for assessment scope and limitations
- Study **`PUBLIC_05_NIST_Gap_Analysis.md`** for NIST CSF 2.0 application
- Examine **`PUBLIC_06_Remediation_Roadmap.md`** for governance and oversight structures
- Reference **`PUBLIC_08_Executive_Summary.md`** for regulatory alignment discussion

### For Enterprise Architects
- Study **`PUBLIC_03_Architecture.md`** for logical design and risk implications
- Review **`PUBLIC_04_Top_10_Risks.md`** for infrastructure resilience risks
- Examine **`PUBLIC_06_Remediation_Roadmap.md`** for architectural improvements (multi-region, PAM, SIEM)
- Reference **`PUBLIC_07_Executive_Dashboard.md`** for resource planning

---

## What This Portfolio Demonstrates

✅ **Risk Assessment & Prioritization**
- 5×5 Likelihood × Impact matrix with residual risk judgment
- Prioritization across 10 risks with timeline and business justification
- Connection between technical risks and business impact

✅ **NIST CSF 2.0 Application**
- Assessment of organizational maturity against official NIST CSF 2.0 Functions
- Identification of gaps across all six Functions (Govern, Identify, Protect, Detect, Respond, Recover)
- Mapping of 10 risks to official NIST identifiers (14 of 22 official Subcategories)
- Maturity roadmap from 1.8 → 2.8 of 5.0

✅ **Business-Driven Security Strategy**
- Phased approach respecting dependencies and resource constraints
- Connection between security investment and business outcome
- Regulatory alignment and board-level governance
- RTO/RPO and critical process mapping

✅ **Remediation Planning & Execution**
- 4-phase roadmap with clear milestones, owners, timelines, costs
- Resource planning and staffing model
- Success metrics and progress tracking
- Risk acceptance framework and board reporting cadence

✅ **Executive Communication**
- Executive summary suitable for board discussion
- Risk acceptance and compliance posture assessment
- Investment justification and expected outcomes
- Recommended voting resolutions

---

## What This Portfolio Does NOT Demonstrate

❌ Penetration testing or detailed vulnerability assessment  
❌ Compliance audit (FDIC, GLBA, BSA/AML)  
❌ Application security review or code analysis  
❌ Detailed incident forensics or threat hunting  
❌ Physical security assessment  
❌ Detailed procurement or vendor comparison (business cases, RFPs)  
❌ Complete IT asset inventory (infrastructure is architectural, not comprehensive)  

---

## Key Learnings

### Assessment & Analysis
- Risk prioritization requires understanding both **likelihood** and **business impact**; residual risk depends on control effectiveness
- NIST CSF 2.0 is a **maturity framework**, not a compliance checklist; organizations typically start at 1.0–1.5 and advance to 2.5–3.0 over 12–24 months
- Financial services threats (ransomware, credential compromise) are **industry-specific**; assessment must reflect threat landscape

### Architecture & Design
- Cloud adoption introduces **new risk vectors** (S3 misconfiguration, IAM policy errors, incomplete logging); AWS Config and CloudTrail are foundational controls
- **Backup resilience** is non-negotiable; untested backup systems provide false assurance; quarterly restoration testing is table-stakes
- **Identity architecture** must separate workforce (Entra ID) from customer authentication; single-directory approaches create unnecessary risk

### Remediation & Execution
- **Phased approach** respects dependencies (governance → controls → testing → optimization) and resource constraints
- **Quick wins** (MFA enforcement, 30-day timeline) build organizational momentum and demonstrate security's value
- **Long-duration initiatives** (PAM, threat hunting, 6–9 month timelines) require executive commitment and budget approval upfront; delays cascade across phases

### Governance & Board Communication
- Security strategy requires **board-level oversight** (steering committee, quarterly reporting, risk acceptance authority)
- **Risk acceptance** decisions must be explicit and documented; deferring low-priority risks (e.g., multi-region failover) is acceptable when business case doesn't justify cost
- **Regulatory alignment** is implicit in well-designed security strategy; FDIC expectations align with NIST CSF maturity and risk management discipline

---

## Repository Structure

```
PUBLIC_README.md                    ← Start here
PUBLIC_01_Disclaimer.md             ← Scope & limitations
PUBLIC_02_Company_Scenario.md       ← Business context & methodology
PUBLIC_03_Architecture.md           ← System design & infrastructure
PUBLIC_04_Top_10_Risks.md          ← Risk register & prioritization
PUBLIC_05_NIST_Gap_Analysis.md     ← Maturity assessment
PUBLIC_06_Remediation_Roadmap.md   ← 12-month execution plan
PUBLIC_07_Executive_Dashboard.md   ← Progress tracking & metrics
PUBLIC_08_Executive_Summary.md     ← Board-level summary
PUBLIC_INDEX.md                     ← This file (navigation guide)
```

---

## Contact & Questions

This portfolio represents a simulated but realistic assessment of a mid-market financial services organization. All findings, risks, and recommendations are designed to reflect industry best practices and NIST CSF 2.0 governance framework.

For questions or feedback:
- Review the **Disclaimer** for scope and intended use
- Consult the README for methodology and learning objectives
- Examine individual documents for detailed findings and recommendations

---

**Portfolio Version:** 1.0 Complete  
**Assessment Framework:** NIST Cybersecurity Framework 2.0  
**Total Pages:** ~18–22 (1,622 lines; 94K markdown)  
**Last Updated:** October 7, 2026  
