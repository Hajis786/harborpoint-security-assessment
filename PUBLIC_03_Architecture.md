# Architecture Summary

## Logical Architecture

HarborPoint operates across three primary domains:

1. **External/Customer Domain** — Internet-facing customer portal and mobile access
2. **Enterprise Domain** — Internal employee systems, identity, and cloud infrastructure
3. **Data Domain** — Databases, backup, and sensitive data repositories

```
┌─────────────────────────────────────────────────────────────────────┐
│                         Internet & Customer Access                   │
│                                                                       │
│  Customer (Browser/Mobile) ──HTTPS──> AWS WAF ──> ALB ──> Portal   │
└─────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────┐
│                      AWS Cloud Infrastructure                         │
│                                                                       │
│  ┌─ Portal/Application Backend (EC2)                                 │
│  ├─ RDS PostgreSQL (Read-Only Replica) ←─ Async from Primary        │
│  ├─ S3 Storage (Backups, Documents)                                  │
│  ├─ AWS IAM (Identity & Access Control)                              │
│  ├─ CloudTrail & CloudWatch (Logging)                                │
│  └─ Client VPN (Remote Access)                                       │
└─────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────┐
│                    On-Premises Infrastructure                        │
│                                                                       │
│  ┌─ PostgreSQL Primary Database (Customer Data)                      │
│  ├─ Veeam Backup System (Daily Full + Incremental)                   │
│  ├─ Fortinet FortiGate Firewall (HQ)                                 │
│  ├─ Consumer Firewalls (Branches)                                    │
│  └─ Splunk Enterprise SIEM                                           │
└─────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────┐
│              Employee Systems & Identity Management                  │
│                                                                       │
│  ┌─ Microsoft Entra ID (Workforce Identity)                          │
│  ├─ Windows 11 Endpoints (160 devices)                               │
│  ├─ CrowdStrike Falcon (Endpoint Detection & Response)               │
│  ├─ Intune (Endpoint & Mobile Device Management)                     │
│  └─ Microsoft 365 (Email, Collaboration)                             │
└─────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────┐
│                    Business Applications                             │
│                                                                       │
│  ├─ Salesforce CRM (Lending Pipeline)                                │
│  ├─ QuickBooks Online (Accounting)                                   │
│  ├─ GitHub (Source Code)                                             │
│  ├─ Payment Processor (Customer Transactions)                        │
│  ├─ ADP (Payroll)                                                    │
│  └─ Proofpoint (Email Archiving)                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Critical Data Flows

**Customer Portal Login & Transaction:**
```
Customer → AWS WAF → ALB → Portal (EC2) 
→ Entra ID (MFA) → RDS (Read-Only Query) 
→ Payment Processor API → Payment Confirmation 
→ Transaction Recorded in PostgreSQL Primary
```

**Employee Access to Customer Data:**
```
Employee → Windows 11 → Entra ID (Authenticate) 
→ AWS Client VPN → Conditional Access Check 
→ Salesforce CRM (API Integration with Portal Backend)
→ Backend Accesses PostgreSQL Primary (Authorized)
→ CrowdStrike (Monitor) → Splunk (Log)
```

**Backup & Disaster Recovery:**
```
PostgreSQL Primary → Veeam Backup (Daily + Incremental)
→ S3 Replication (Cross-Region Availability)

Portal Application → EBS Snapshots → S3
```

**Security Monitoring:**
```
All Systems → Portal Events, CrowdStrike Telemetry, CloudTrail Logs, Entra Auth Logs
→ Splunk SIEM (Centralized)
→ Incident Response Team (Manual Investigation)
```

---

## Single Points of Failure

| Dependency | Risk | Current Mitigation |
|-----------|------|-------------------|
| Entra ID | External SaaS; ISP outage blocks authentication | Depends on ISP and Microsoft availability; no on-premises fallback |
| PostgreSQL Primary | Hardware failure; data loss | RDS async replica; Veeam backups; last restoration test April 2025 (overdue) |
| ISP (HQ) | Carrier outage | Dual ISP with automatic failover |
| ISP (Branches) | Carrier outage | Single ISP per branch; dependent on HQ VPN for failover |
| AWS Region | AWS infrastructure failure | Single region; no multi-region failover |
| Backup System | Veeam hardware failure; ransomware encryption | No documented failover; restoration testing overdue |
| Portal Application | EC2 crash | Load balancer; no standby instance documented |

---

## Network Segmentation

**HQ Location:**
- DMZ: Firewall → Internet egress
- Internal Network: Endpoints, servers, printers
- Data Center: Database server, backup appliances
- Wireless: Guest and employee WiFi

**Branch Locations (Virginia, Pennsylvania):**
- Consumer-grade firewalls (basic packet filtering)
- No SD-WAN deployment (single ISP per location)
- Dependent on HQ for backup Internet connectivity

**AWS Cloud:**
- Public Subnets: WAF, ALB, NAT Gateway
- Private Subnets: EC2 Portal/Backend
- Database Subnets: RDS Read-Only Replica
- Security Groups: Per-tier ingress/egress rules
- Network ACLs: Stateless boundary rules

---

## Identity Architecture

**Workforce Identity (Microsoft Entra ID):**
- Centralized identity provider for employees and administrators
- Conditional Access policies for Windows 11, M365, AWS IAM, Salesforce, VPN
- MFA enforcement incomplete; some admin roles allow password-only access
- Service accounts stored in configuration files (no PAM platform)

**Customer Portal Authentication:**
- Application-level identity (separate from workforce Entra ID)
- Username/Password + MFA (SMS/App) for 40,000 bank customers
- Portal manages customer session and credential storage

---

## Architecture Gaps & Risks

1. **No multi-region failover** — AWS portal in single region; branch locations dependent on single ISP
2. **Backup restoration untested** — Last documented full restoration: April 2025 (18 months prior)
3. **Service account credentials unmanaged** — Stored in configuration files; no secrets platform
4. **CloudTrail logging incomplete** — Enabled but logs not centralized to SIEM for alerting
5. **Third-party risk not formalized** — Salesforce, ADP, payment processor integrations lack formal risk assessment
6. **Email security** — Proofpoint provides archival only; inbound email filtering relies on M365 defaults
7. **IAM audit logging incomplete** — CloudTrail exists but not fully centralized or alerted on
8. **Database replication not optimized** — RDS async replica; RPO/RTO not measured

---

**Next: Top 10 Risks & Remediation Priorities**
