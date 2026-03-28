# CIS Controls v8 IG1 - Control Family Summary

**Document Classification:** Internal - Security Program  
**Version:** 1.0  
**Date:** March 2026  
**Author:** Jelani D. Maitland  
**Context:** MedCaribe Health Group

---

## 1. Purpose

This document provides a summary-level view of each CIS Controls v8 control family, its relevance to MedCaribe Health Group, and how well Microsoft 365 Business Premium addresses the IG1 safeguards within each family. Use this as a quick reference before diving into the detailed safeguard-level mapping.

---

## 2. Control Family Summaries

### Control 1 - Inventory and Control of Enterprise Assets

| Field | Detail |
|-------|--------|
| **IG1 Safeguards** | 2 (1.1, 1.2) |
| **M365 Coverage** | Partial |
| **Primary M365 Tools** | Intune (device inventory), Entra ID (registered devices), Conditional Access (block unmanaged devices) |
| **What M365 Covers** | Inventory and management of enrolled endpoints (workstations, laptops, mobile devices). Conditional Access can block unregistered devices from accessing M365 services. |
| **Gaps** | Network devices (routers, switches, access points), printers, IoT devices, and any assets not enrolled in Intune are not inventoried. A supplementary manual inventory is required. |
| **MedCaribe Priority** | High - no formal asset inventory exists |

---

### Control 2 - Inventory and Control of Software Assets

| Field | Detail |
|-------|--------|
| **IG1 Safeguards** | 3 (2.1, 2.2, 2.3) |
| **M365 Coverage** | Full to Partial |
| **Primary M365 Tools** | Intune (discovered apps, app management), Defender for Business (software inventory, vulnerability tracking) |
| **What M365 Covers** | Automatic software discovery on managed endpoints. App deployment and restriction policies. Vulnerability identification for installed software. |
| **Gaps** | End-of-support status detection requires manual vendor lifecycle review. Software on non-enrolled devices is not visible. |
| **MedCaribe Priority** | Medium - shadow IT identified in Project 1 (personal Google Drive, unauthorized apps) |

---

### Control 3 - Data Protection

| Field | Detail |
|-------|--------|
| **IG1 Safeguards** | 10 (3.1, 3.2, 3.3, 3.4, 3.5, 3.6, 3.7, 3.9, 3.10, 3.11, 3.12) |
| **M365 Coverage** | Mostly Full |
| **Primary M365 Tools** | Purview (classification, retention, DLP), Intune (BitLocker, device control), Exchange Online (TLS), SharePoint (permissions, sensitivity labels) |
| **What M365 Covers** | Data classification and labelling, encryption at rest and in transit, retention policies, access controls, endpoint encryption (BitLocker), removable media encryption, and data segmentation via SharePoint sites. |
| **Gaps** | Data in third-party SaaS (CloudMed EHR, QuickBooks) is outside M365 Purview visibility. Physical document disposal is a process control, not a technology one. |
| **MedCaribe Priority** | Critical - patient data handling is the organization's highest regulatory exposure. Data Classification Policy (POL-004) provides governance foundation; M365 provides enforcement. |

---

### Control 4 - Secure Configuration of Enterprise Assets and Software

| Field | Detail |
|-------|--------|
| **IG1 Safeguards** | 3 (4.1, 4.3, 4.7) |
| **M365 Coverage** | Full to Partial |
| **Primary M365 Tools** | Intune (Security Baselines, configuration profiles), Defender for Business (Secure Score recommendations), Windows LAPS |
| **What M365 Covers** | Pre-built security baselines for Windows and Edge. Screen lock timeout enforcement. Local admin password management (LAPS). Ongoing configuration recommendations via Secure Score. |
| **Gaps** | Default credentials on printers, routers, and NAS devices are outside M365 scope and must be addressed manually. |
| **MedCaribe Priority** | High - no hardening standards exist; printers likely retain factory defaults |

---

### Control 5 - Account Management

| Field | Detail |
|-------|--------|
| **IG1 Safeguards** | 4 (5.1, 5.2, 5.3, 5.4) |
| **M365 Coverage** | Mostly Full |
| **Primary M365 Tools** | Entra ID (user management, role assignments, sign-in logs, password protection, dormant account detection) |
| **What M365 Covers** | Complete account lifecycle management for M365 identities. Password policies and banned password lists. Dormant account identification via sign-in activity. Dedicated admin account separation. |
| **Gaps** | Password uniqueness across non-M365 systems (EHR, QuickBooks, insurance portals) cannot be enforced by M365. Password manager deployment is a supplementary recommendation. |
| **MedCaribe Priority** | Critical - shared accounts, no offboarding process, and excessive admin privileges were top risks in Project 1 |

---

### Control 6 - Access Management

| Field | Detail |
|-------|--------|
| **IG1 Safeguards** | 5 (6.1, 6.2, 6.3, 6.4, 6.5) |
| **M365 Coverage** | Full |
| **Primary M365 Tools** | Entra ID (Conditional Access, MFA, role assignments, group-based access, session revocation), Intune (remote wipe) |
| **What M365 Covers** | Complete access granting and revoking lifecycle. MFA for all users, remote access, and admin accounts. Conditional Access policies for location-based, device-based, and risk-based access decisions. |
| **Gaps** | None for M365-managed resources. Third-party systems (EHR, QuickBooks) require their own access management. |
| **MedCaribe Priority** | Critical - MFA enforcement is the single highest-impact control. Identified as Phase 1 Quick Win in Project 1. |

---

### Control 7 - Continuous Vulnerability Management

| Field | Detail |
|-------|--------|
| **IG1 Safeguards** | 4 (7.1, 7.2, 7.3, 7.4) |
| **M365 Coverage** | Full to Partial |
| **Primary M365 Tools** | Defender for Business (Threat and Vulnerability Management), Intune (Windows Update rings, app deployment) |
| **What M365 Covers** | Automatic vulnerability identification and prioritization on managed endpoints. Automated OS patching via Windows Update for Business. M365 Apps auto-update. |
| **Gaps** | Third-party application patching outside of Intune-managed apps requires manual processes or additional tooling. |
| **MedCaribe Priority** | High - no centralized patch management exists |

---

### Control 8 - Audit Log Management

| Field | Detail |
|-------|--------|
| **IG1 Safeguards** | 4 (8.1, 8.2, 8.3, 8.5) |
| **M365 Coverage** | Full |
| **Primary M365 Tools** | M365 Unified Audit Log, Entra ID sign-in logs, Defender for Business (device timeline), Purview Audit |
| **What M365 Covers** | Comprehensive audit logging across all M365 services. 180-day retention (Business Premium). Detailed event capture including user, timestamp, IP, action, and result. |
| **Gaps** | Network device logs, third-party SaaS logs (EHR, QuickBooks) are outside M365 scope. Extended retention beyond 180 days requires Audit Premium add-on or log export. |
| **MedCaribe Priority** | High - audit logging has never been enabled or reviewed. Identified as Phase 1 Quick Win in Project 1. |

---

### Control 9 - Email and Web Browser Protections

| Field | Detail |
|-------|--------|
| **IG1 Safeguards** | 4 (9.2, 9.5, 9.6, 9.7) |
| **M365 Coverage** | Mostly Full |
| **Primary M365 Tools** | Exchange Online Protection (anti-malware, attachment filtering), Defender for Office 365 (Safe Attachments, Safe Links), Defender for Business (web content filtering) |
| **What M365 Covers** | Email anti-malware scanning and sandboxing. Dangerous attachment type blocking. DMARC/DKIM/SPF configuration support. Web content filtering on managed endpoints. |
| **Gaps** | True DNS-level filtering for the entire network (all devices, not just managed endpoints) requires a network-level DNS filtering service. |
| **MedCaribe Priority** | Critical - email is the primary attack vector for healthcare organizations |

---

### Control 10 - Malware Defenses

| Field | Detail |
|-------|--------|
| **IG1 Safeguards** | 4 (10.1, 10.2, 10.3, 10.4) |
| **M365 Coverage** | Full |
| **Primary M365 Tools** | Defender for Business (next-gen antivirus, EDR, cloud-delivered protection), Intune (antivirus policies, device control) |
| **What M365 Covers** | Anti-malware deployment with automatic signature updates. Cloud-delivered protection for near-real-time detection. Autorun/autoplay disabling. Removable media scanning. |
| **Gaps** | None for enrolled endpoints. Unenrolled devices (reception tablets on consumer Android) do not benefit from centralized malware management. |
| **MedCaribe Priority** | High - Defender exists on Windows devices but is not centrally managed via Defender for Business |

---

### Control 11 - Data Recovery

| Field | Detail |
|-------|--------|
| **IG1 Safeguards** | 4 (11.1, 11.2, 11.3, 11.4) |
| **M365 Coverage** | Mostly None - critical gap |
| **Primary M365 Tools** | Native M365 retention (OneDrive versioning, Exchange recovery) provides minimal coverage only |
| **What M365 Covers** | OneDrive file versioning and SharePoint recycle bin provide limited self-service recovery. Exchange Online has deleted items recovery (14-30 days). |
| **Gaps** | M365 does not provide true independent backup, automated backup, encrypted backup storage, or immutable/air-gapped backup. All four safeguards require a third-party M365 backup solution. |
| **MedCaribe Priority** | Critical - this is the biggest M365 gap. Ransomware recovery capability depends entirely on implementing third-party backup. Budget: TTD 800-1,500/month. |

---

### Control 12 - Network Infrastructure Management

| Field | Detail |
|-------|--------|
| **IG1 Safeguards** | 2 (12.1, 12.6) |
| **M365 Coverage** | Partial to None |
| **Primary M365 Tools** | Defender for Business (network protection on managed endpoints - partial DNS filtering) |
| **What M365 Covers** | Endpoint-level web content filtering and network protection block malicious URLs on managed devices. |
| **Gaps** | Router/switch/access point firmware updates, network segmentation, and network-wide DNS filtering are entirely outside M365 scope. These require direct infrastructure management. |
| **MedCaribe Priority** | High - consumer-grade routers, no VLANs, shared staff/guest Wi-Fi. Phase 4 of Project 1 roadmap addresses with firewall deployment. |

---

### Control 13 - Network Monitoring and Defense

| Field | Detail |
|-------|--------|
| **IG1 Safeguards** | 1 (13.1) |
| **M365 Coverage** | Full (within M365 ecosystem) |
| **Primary M365 Tools** | Microsoft 365 Defender portal (unified incident queue, cross-service alerting) |
| **What M365 Covers** | Centralized alerting across email, identity, and endpoint security within M365. Unified incident view correlating related alerts. |
| **Gaps** | Does not capture alerts from network infrastructure, third-party SaaS, or physical security systems. For a small organization, this coverage is adequate. |
| **MedCaribe Priority** | Medium - no alerting of any kind currently exists |

---

### Control 14 - Security Awareness and Skills Training

| Field | Detail |
|-------|--------|
| **IG1 Safeguards** | 6 (14.1, 14.2, 14.3, 14.4, 14.5, 14.8) |
| **M365 Coverage** | Mostly Full |
| **Primary M365 Tools** | Defender for Office 365 (Attack Simulation Training - phishing simulations, training modules), Exchange Online (Report Message add-in, MailTips) |
| **What M365 Covers** | Phishing simulation campaigns. Built-in training modules for social engineering, authentication, and data handling. Suspicious email reporting button for Outlook. External recipient warnings via MailTips. |
| **Gaps** | MedCaribe-specific training content (aligned to POL-001, POL-004, and the Data Protection Act) needs to be created or sourced separately. M365 training content covers general topics but not organizational policies. |
| **MedCaribe Priority** | Critical - zero training has ever been delivered. Identified as Phase 3 action in Project 1. |

---

### Control 15 - Service Provider Management

| Field | Detail |
|-------|--------|
| **IG1 Safeguards** | 2 (15.1, 15.4) |
| **M365 Coverage** | Partial to None |
| **Primary M365 Tools** | Entra ID (Enterprise Applications - shows OAuth-connected apps) |
| **What M365 Covers** | Visibility into third-party apps connected to M365 via OAuth. Microsoft's own DPA satisfies contractual requirements for the Microsoft vendor relationship. |
| **Gaps** | Vendor inventory, risk tiering, and contractual security requirements for non-M365 vendors (EHR, QuickBooks, insurance, labs) are governance activities outside M365 scope. Covered by POL-005 from Project 1. |
| **MedCaribe Priority** | High - no vendor assessments have ever been conducted |

---

### Control 16 - Application Software Security

| Field | Detail |
|-------|--------|
| **IG1 Safeguards** | 2 (16.1, 16.11) |
| **M365 Coverage** | Not Applicable |
| **Primary M365 Tools** | N/A |
| **What M365 Covers** | N/A |
| **Gaps** | N/A - MedCaribe does not develop software or operate database servers. All applications are commercial off-the-shelf or SaaS. |
| **MedCaribe Priority** | N/A - reassess if custom development is introduced |

---

### Control 17 - Incident Response Management

| Field | Detail |
|-------|--------|
| **IG1 Safeguards** | 7 (17.1, 17.2, 17.3, 17.4, 17.5, 17.6, 17.7, 17.9) |
| **M365 Coverage** | Partial to None (governance-heavy control) |
| **Primary M365 Tools** | Defender for Office 365 (Attack Simulation Training for exercises, Report Message add-in for reporting) |
| **What M365 Covers** | Phishing simulation for exercise component. Email reporting button for incident reporting. M365 Defender portal provides investigation tools during incidents. |
| **Gaps** | Most IR safeguards are governance, documentation, and process controls that cannot be satisfied by technology alone. The IR Plan, Escalation Decision Tree, severity thresholds, team assignments, and contact lists from Project 1 satisfy these safeguards. |
| **MedCaribe Priority** | Addressed by Project 1 - IR Plan and supporting documents satisfy 5 of 7 safeguards. Remaining 2 require exercise execution and technical tool deployment. |

---

## 3. Coverage Heatmap

| Control Family | Full | Partial | None | N/A | Overall |
|---------------|------|---------|------|-----|---------|
| 1. Asset Inventory | 0 | 2 | 0 | 0 | PARTIAL |
| 2. Software Inventory | 1 | 1 | 0 | 1 | PARTIAL |
| 3. Data Protection | 7 | 3 | 0 | 0 | STRONG |
| 4. Secure Configuration | 2 | 1 | 0 | 0 | STRONG |
| 5. Account Management | 3 | 1 | 0 | 0 | STRONG |
| 6. Access Management | 5 | 0 | 0 | 0 | FULL |
| 7. Vulnerability Management | 3 | 1 | 0 | 0 | STRONG |
| 8. Audit Log Management | 4 | 0 | 0 | 0 | FULL |
| 9. Email/Web Protections | 3 | 1 | 0 | 0 | STRONG |
| 10. Malware Defenses | 4 | 0 | 0 | 0 | FULL |
| 11. Data Recovery | 0 | 1 | 3 | 0 | WEAK |
| 12. Network Infrastructure | 0 | 1 | 1 | 0 | WEAK |
| 13. Network Monitoring | 1 | 0 | 0 | 0 | FULL |
| 14. Security Awareness | 5 | 1 | 0 | 0 | STRONG |
| 15. Service Provider Mgmt | 0 | 1 | 1 | 0 | WEAK |
| 16. Application Security | 0 | 0 | 0 | 2 | N/A |
| 17. Incident Response | 0 | 3 | 4 | 0 | GOVERNANCE |

---

## 4. Document Control

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | March 2026 | J. Maitland | Initial summary |
