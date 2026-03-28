# CIS Controls v8 IG1 — Implementation Tracker

**Document Classification:** Internal — IT and Management  
**Version:** 1.0  
**Date:** March 2026  
**Author:** Jelani D. Maitland  
**Context:** MedCaribe Health Group  
**Review Cycle:** Monthly during implementation; quarterly once baseline is established

---

## 1. Purpose

This tracker provides an operational view of implementation status for each CIS Controls v8 IG1 safeguard at MedCaribe Health Group. It is designed to be used by the IT Administrator and Operations Manager to track progress, assign ownership, and prioritize work.

---

## 2. Status Definitions

| Status | Definition |
|--------|------------|
| Implemented | Safeguard is fully configured and operational |
| In Progress | Implementation has started but is not complete |
| Planned | Scheduled for a specific phase but work has not started |
| Not Started | No action taken; not yet scheduled |
| Not Applicable | Safeguard does not apply to MedCaribe's environment |

---

## 3. Priority Definitions

| Priority | Definition |
|----------|------------|
| P1 — Immediate | Addresses Critical risk; zero or minimal cost; implement in Phase 1 (Weeks 1-4) |
| P2 — Foundation | Addresses High risk; requires some configuration or budget; Phase 2 (Months 2-3) |
| P3 — Capability | Builds operational capability; Phase 3 (Months 4-6) |
| P4 — Maturity | Long-term hardening and improvement; Phase 4 (Months 7-12) |

---

## 4. Implementation Tracker

### Control 1 — Inventory and Control of Enterprise Assets

| ID | Safeguard | M365 Coverage | Status | Priority | Owner | Target Date | Notes |
|----|-----------|--------------|--------|----------|-------|-------------|-------|
| 1.1 | Enterprise asset inventory | Partial | Not Started | P2 | IT Admin | Month 2 | Enroll devices in Intune; create supplementary spreadsheet for network devices |
| 1.2 | Address unauthorized assets | Partial | Not Started | P3 | IT Admin | Month 4 | Configure Conditional Access to require managed devices |

### Control 2 — Inventory and Control of Software Assets

| ID | Safeguard | M365 Coverage | Status | Priority | Owner | Target Date | Notes |
|----|-----------|--------------|--------|----------|-------|-------------|-------|
| 2.1 | Software inventory | Full | Not Started | P2 | IT Admin | Month 2 | Onboard endpoints to Defender for Business for auto-discovery |
| 2.2 | Ensure software is supported | Partial | Not Started | P3 | IT Admin | Month 5 | Manual review of software lifecycle after inventory is built |
| 2.3 | Address unauthorized software | Full | Not Started | P3 | IT Admin | Month 5 | Configure Intune app control after software inventory is complete |

### Control 3 — Data Protection

| ID | Safeguard | M365 Coverage | Status | Priority | Owner | Target Date | Notes |
|----|-----------|--------------|--------|----------|-------|-------------|-------|
| 3.1 | Data management process | Partial | Implemented | — | Ops Manager | Complete | POL-004 from Project 1 satisfies documentation requirement |
| 3.2 | Data inventory | Partial | Not Started | P3 | IT Admin | Month 4 | Configure Purview content explorer for M365 data |
| 3.3 | Data access control lists | Full | Not Started | P2 | IT Admin | Month 2 | Configure SharePoint permissions aligned to POL-002 access matrix |
| 3.4 | Enforce data retention | Full | Not Started | P3 | IT Admin | Month 4 | Configure Purview retention policies per POL-004 retention schedule |
| 3.5 | Securely dispose of data | Partial | Not Started | P3 | IT Admin + Ops Mgr | Month 5 | Configure Purview disposition review; establish physical disposal process |
| 3.6 | Encrypt end-user devices | Full | Not Started | P1 | IT Admin | Week 2 | Enable BitLocker via Intune — zero cost, Phase 1 Quick Win |
| 3.7 | Data classification scheme | Full | Implemented | — | Ops Manager | Complete | POL-004 defines 4-tier classification. Purview labels to be configured in P3 |
| 3.9 | Encrypt removable media | Full | Not Started | P2 | IT Admin | Month 3 | Enforce BitLocker To Go or block USB storage via Intune |
| 3.10 | Encrypt data in transit | Full | Implemented | — | N/A | Complete | M365 enforces TLS 1.2 by default for all services |
| 3.11 | Encrypt data at rest | Full | Implemented | — | N/A | Complete | M365 encrypts all data at rest by default (AES-256) |
| 3.12 | Segment data by sensitivity | Full | Not Started | P3 | IT Admin + Ops Mgr | Month 5 | Create separate SharePoint sites with sensitivity labels |

### Control 4 — Secure Configuration

| ID | Safeguard | M365 Coverage | Status | Priority | Owner | Target Date | Notes |
|----|-----------|--------------|--------|----------|-------|-------------|-------|
| 4.1 | Secure configuration process | Full | Not Started | P2 | IT Admin | Month 2 | Deploy Intune Security Baselines for Windows and Edge |
| 4.3 | Auto session locking | Full | Not Started | P1 | IT Admin | Week 2 | Configure 10-min screen lock via Intune (per POL-002) |
| 4.7 | Manage default accounts | Partial | Not Started | P3 | IT Admin | Month 4 | Deploy Windows LAPS via Intune; manually change printer/NAS defaults |

### Control 5 — Account Management

| ID | Safeguard | M365 Coverage | Status | Priority | Owner | Target Date | Notes |
|----|-----------|--------------|--------|----------|-------|-------------|-------|
| 5.1 | Account inventory | Full | Partial | P1 | IT Admin | Week 1 | Entra ID user list exists; needs formal review process |
| 5.2 | Unique passwords | Partial | Not Started | P2 | IT Admin + Ops Mgr | Month 2 | Enable Entra ID password protection; recommend password manager to staff |
| 5.3 | Disable dormant accounts | Full | Not Started | P1 | IT Admin | Week 3 | Review Entra ID for accounts with no sign-in in 45+ days |
| 5.4 | Dedicated admin accounts | Full | Not Started | P1 | IT Admin | Week 1 | Create admin.doyle@ and admin.rampersad@ — Phase 1 Quick Win |

### Control 6 — Access Management

| ID | Safeguard | M365 Coverage | Status | Priority | Owner | Target Date | Notes |
|----|-----------|--------------|--------|----------|-------|-------------|-------|
| 6.1 | Access granting process | Full | Not Started | P2 | IT Admin + Ops Mgr | Month 2 | Implement group-based access per POL-002 role matrix |
| 6.2 | Access revoking process | Full | Not Started | P1 | IT Admin + Ops Mgr | Week 2 | Implement offboarding checklist — Phase 1 Quick Win |
| 6.3 | MFA for external apps | Full | Not Started | P1 | IT Admin | Week 1 | Enforce MFA for all users — #1 highest-impact control |
| 6.4 | MFA for remote access | Full | Not Started | P1 | IT Admin | Week 1 | Covered by 6.3 for a cloud-first organization |
| 6.5 | MFA for admin access | Full | Partial | P1 | IT Admin | Week 1 | Extend MFA to dedicated admin accounts |

### Control 7 — Continuous Vulnerability Management

| ID | Safeguard | M365 Coverage | Status | Priority | Owner | Target Date | Notes |
|----|-----------|--------------|--------|----------|-------|-------------|-------|
| 7.1 | Vulnerability management process | Full | Not Started | P2 | IT Admin | Month 2 | Onboard endpoints to Defender for Business TVM |
| 7.2 | Remediation process | Full | Not Started | P2 | IT Admin | Month 3 | Establish monthly review of Defender remediation recommendations |
| 7.3 | Automated OS patching | Full | Not Started | P2 | IT Admin | Month 2 | Configure Windows Update rings in Intune |
| 7.4 | Automated app patching | Partial | Not Started | P2 | IT Admin | Month 3 | Enable M365 Apps auto-update; manual process for third-party apps |

### Control 8 — Audit Log Management

| ID | Safeguard | M365 Coverage | Status | Priority | Owner | Target Date | Notes |
|----|-----------|--------------|--------|----------|-------|-------------|-------|
| 8.1 | Audit log management process | Full | Not Started | P1 | IT Admin | Week 3 | Document log review cadence (weekly) and retention (180 days) |
| 8.2 | Collect audit logs | Full | Not Started | P1 | IT Admin | Week 3 | Enable M365 Unified Audit Log — Phase 1 Quick Win |
| 8.3 | Adequate log storage | Full | Not Started | P1 | IT Admin | Week 3 | 180-day retention is adequate for IG1; evaluate extension later |
| 8.5 | Detailed audit logs | Full | Not Started | P1 | IT Admin | Week 3 | Enabled automatically when Unified Audit Log is turned on |

### Control 9 — Email and Web Browser Protections

| ID | Safeguard | M365 Coverage | Status | Priority | Owner | Target Date | Notes |
|----|-----------|--------------|--------|----------|-------|-------------|-------|
| 9.2 | DNS filtering | Partial | Not Started | P4 | IT Admin | Month 8 | Enable Defender network protection on endpoints; evaluate network-level DNS later |
| 9.5 | Implement DMARC | Full | Not Started | P2 | IT Admin | Month 3 | Configure SPF, DKIM, DMARC DNS records; start with p=none |
| 9.6 | Block unnecessary file types | Full | Not Started | P1 | IT Admin | Week 2 | Enable common attachment filter in EOP — Phase 1 Quick Win |
| 9.7 | Email anti-malware | Full | Not Started | P1 | IT Admin | Week 2 | Enable Safe Attachments policy — Phase 1 Quick Win |

### Control 10 — Malware Defenses

| ID | Safeguard | M365 Coverage | Status | Priority | Owner | Target Date | Notes |
|----|-----------|--------------|--------|----------|-------|-------------|-------|
| 10.1 | Deploy anti-malware | Full | Partial | P2 | IT Admin | Month 2 | Windows Defender exists; onboard to Defender for Business for centralized management |
| 10.2 | Automatic signature updates | Full | Partial | P2 | IT Admin | Month 2 | Auto-updates work; verify cloud-delivered protection is enabled via Intune |
| 10.3 | Disable autorun/autoplay | Full | Not Started | P2 | IT Admin | Month 2 | Configure via Intune device configuration profile |
| 10.4 | Scan removable media | Full | Not Started | P2 | IT Admin | Month 2 | Enable in Defender Antivirus policy via Intune |

### Control 11 — Data Recovery

| ID | Safeguard | M365 Coverage | Status | Priority | Owner | Target Date | Notes |
|----|-----------|--------------|--------|----------|-------|-------------|-------|
| 11.1 | Data recovery practice | Partial | Not Started | P2 | Ops Manager | Month 2 | Document RTO/RPO per system; verify EHR vendor backup SLA |
| 11.2 | Automated backups | None | Not Started | P2 | IT Admin | Month 2 | REQUIRES THIRD-PARTY BACKUP — budget TTD 800-1,500/month |
| 11.3 | Protect recovery data | None | Not Started | P2 | IT Admin | Month 2 | Select backup provider with encryption and RBAC |
| 11.4 | Isolated recovery data | None | Not Started | P2 | IT Admin | Month 2 | Select backup provider with immutable storage option |

### Control 12 — Network Infrastructure Management

| ID | Safeguard | M365 Coverage | Status | Priority | Owner | Target Date | Notes |
|----|-----------|--------------|--------|----------|-------|-------------|-------|
| 12.1 | Network infrastructure up-to-date | None | Not Started | P4 | IT Admin | Month 7 | Replace consumer routers; update firmware on all network devices |
| 12.6 | DNS filtering services | Partial | Not Started | P4 | IT Admin | Month 8 | Enable Defender network protection; evaluate Cloudflare Gateway |

### Control 13 — Network Monitoring and Defense

| ID | Safeguard | M365 Coverage | Status | Priority | Owner | Target Date | Notes |
|----|-----------|--------------|--------|----------|-------|-------------|-------|
| 13.1 | Centralize security alerting | Full | Not Started | P2 | IT Admin | Month 3 | Configure M365 Defender alert notifications to IT Admin and Ops Manager |

### Control 14 — Security Awareness and Skills Training

| ID | Safeguard | M365 Coverage | Status | Priority | Owner | Target Date | Notes |
|----|-----------|--------------|--------|----------|-------|-------------|-------|
| 14.1 | Security awareness program | Full | Not Started | P3 | Ops Manager | Month 4 | Deploy M365 Attack Simulation Training platform |
| 14.2 | Social engineering training | Full | Not Started | P3 | Ops Manager | Month 4 | Launch first phishing simulation campaign |
| 14.3 | Authentication training | Full | Not Started | P3 | Ops Manager | Month 4 | Deliver with MFA rollout |
| 14.4 | Data handling training | Partial | Not Started | P3 | Ops Manager | Month 5 | Create custom content aligned to POL-001 and POL-004 |
| 14.5 | Unintentional data exposure training | Full | Not Started | P3 | Ops Manager | Month 5 | Configure MailTips; include in awareness program |
| 14.8 | Incident reporting training | Full | Not Started | P3 | Ops Manager | Month 5 | Deploy Report Message add-in; train on IR Policy |

### Control 15 — Service Provider Management

| ID | Safeguard | M365 Coverage | Status | Priority | Owner | Target Date | Notes |
|----|-----------|--------------|--------|----------|-------|-------------|-------|
| 15.1 | Service provider inventory | Partial | Not Started | P3 | Ops Manager | Month 4 | Review Entra ID enterprise apps; maintain full vendor register per POL-005 |
| 15.4 | Security in contracts | None | Not Started | P3 | Ops Manager + Med Dir | Month 5 | Review and update vendor contracts per POL-005 requirements |

### Control 16 — Application Software Security

| ID | Safeguard | M365 Coverage | Status | Priority | Owner | Target Date | Notes |
|----|-----------|--------------|--------|----------|-------|-------------|-------|
| 16.1 | Secure development process | N/A | N/A | N/A | N/A | N/A | MedCaribe does not develop software |
| 16.11 | Database hardening templates | N/A | N/A | N/A | N/A | N/A | All databases are SaaS-managed |

### Control 17 — Incident Response Management

| ID | Safeguard | M365 Coverage | Status | Priority | Owner | Target Date | Notes |
|----|-----------|--------------|--------|----------|-------|-------------|-------|
| 17.1 | Designate IR personnel | None | Implemented | — | Ops Manager | Complete | Defined in Project 1 IR Plan |
| 17.2 | IR contact information | None | Implemented | — | Ops Manager | Complete | Documented in Escalation Decision Tree |
| 17.3 | Incident reporting process | Partial | Implemented | P3 | IT Admin | Month 5 | Policy defined in Project 1; Report Message add-in to be deployed |
| 17.4 | IR process | None | Implemented | — | Ops Manager | Complete | Full IR Plan from Project 1 |
| 17.5 | IR roles and responsibilities | None | Implemented | — | Ops Manager | Complete | Defined in Project 1 IR Plan |
| 17.6 | IR communication mechanisms | Partial | Partial | P3 | Ops Manager | Month 5 | Phone contacts documented; consider Signal group as backup channel |
| 17.7 | Routine IR exercises | Partial | Not Started | P3 | Ops Manager | Month 5 | First tabletop exercise scheduled per Project 1 roadmap |
| 17.9 | Incident severity thresholds | None | Implemented | — | Ops Manager | Complete | Four severity levels defined in IR Policy (POL-003) |

---

## 5. Implementation Summary

| Status | Count | Percentage |
|--------|-------|------------|
| Implemented | 8 | 14% |
| Partial | 3 | 5% |
| Not Started | 41 | 73% |
| Not Applicable | 2 | 4% |
| In Progress | 0 | 0% |
| **Total** | **56** | **100%** |

| Priority | Count | Timeline |
|----------|-------|----------|
| P1 — Immediate | 16 | Weeks 1-4 |
| P2 — Foundation | 18 | Months 2-3 |
| P3 — Capability | 15 | Months 4-6 |
| P4 — Maturity | 3 | Months 7-12 |
| Already Implemented / N/A | 10 | Complete |

---

## 6. Document Control

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | March 2026 | J. Maitland | Initial tracker — baseline status for all 56 safeguards |

**Next Review:** Monthly during active implementation; quarterly once Phase 2 is complete.
