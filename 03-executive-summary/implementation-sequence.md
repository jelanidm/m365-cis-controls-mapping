# CIS Controls v8 IG1 — Recommended Implementation Sequence

**Document Classification:** Confidential — IT and Management  
**Version:** 1.0  
**Date:** March 2026  
**Author:** Jelani D. Maitland  
**Context:** MedCaribe Health Group

---

## 1. Purpose

This document provides the recommended order of implementation for CIS Controls v8 IG1 safeguards at MedCaribe Health Group, using Microsoft 365 Business Premium as the primary platform. The sequence is optimized for maximum risk reduction per unit of effort, starting with zero-cost configuration changes and building toward investments that require budget approval.

---

## 2. Sequencing Principles

Safeguards are ordered by: risk reduction impact (addresses Critical and High risks first), cost (free before paid), dependency (foundational controls that other safeguards depend on come first), and effort (quick configuration changes before complex deployments).

---

## 3. Implementation Waves

### Wave 1 — Identity and Access Lockdown (Week 1)

*Addresses: RISK-001 (BEC), RISK-003 (Unauthorized Access), RISK-007 (Excessive Admin). Cost: TTD $0.*

| Order | Safeguard | Action | Admin Portal |
|-------|-----------|--------|-------------|
| 1 | 6.3 | Enable MFA for all users via Security Defaults or Conditional Access | entra.microsoft.com > Protection > Security defaults (or Conditional Access) |
| 2 | 5.4 | Create dedicated admin accounts (admin.doyle@, admin.rampersad@) | entra.microsoft.com > Users > New user |
| 3 | 6.5 | Assign admin roles only to dedicated admin accounts; remove from daily accounts | entra.microsoft.com > Roles and administrators |
| 4 | 6.2 | Implement offboarding checklist; test account disable and session revocation | entra.microsoft.com > Users > [user] > Block sign-in |
| 5 | 5.3 | Review and disable dormant accounts (no sign-in in 45+ days) | entra.microsoft.com > Users > filter by last sign-in |
| 6 | 5.1 | Export and review full account list; document as baseline inventory | entra.microsoft.com > Users > All users > Export |

**Wave 1 outcome:** The most critical vulnerability (credential compromise) is closed. Admin accounts are separated. Dormant accounts eliminated. Account baseline established.

---

### Wave 2 — Email and Data Protection (Week 2-3)

*Addresses: RISK-005 (Phishing), RISK-016 (Email Forwarding), RISK-013 (Unencrypted Data). Cost: TTD $0.*

| Order | Safeguard | Action | Admin Portal |
|-------|-----------|--------|-------------|
| 7 | 9.7 | Enable Safe Attachments policy (Dynamic Delivery mode) | security.microsoft.com > Threat policies > Safe Attachments |
| 8 | 9.6 | Enable Common Attachment Types filter in anti-malware policy | security.microsoft.com > Threat policies > Anti-malware |
| 9 | 3.6 | Enable BitLocker enforcement via Intune disk encryption policy | intune.microsoft.com > Endpoint security > Disk encryption |
| 10 | 4.3 | Configure 10-minute screen lock timeout via Intune | intune.microsoft.com > Devices > Configuration profiles |
| 11 | 3.10 | Verify TLS 1.2 enforcement (enabled by default; confirm) | admin.exchange.microsoft.com > Mail flow > Connectors |
| 12 | 14.5 | Configure MailTips for external recipient warnings | admin.exchange.microsoft.com > Mail flow > Rules |

**Wave 2 outcome:** Email attack surface is hardened. Endpoint data is encrypted. Accidental external sharing gets a warning prompt.

---

### Wave 3 — Audit and Visibility (Week 3-4)

*Addresses: RISK-018 (No Logging). Cost: TTD $0.*

| Order | Safeguard | Action | Admin Portal |
|-------|-----------|--------|-------------|
| 13 | 8.2 | Enable M365 Unified Audit Log | compliance.microsoft.com > Audit |
| 14 | 8.5 | Verify detailed logging is active (automatic once 8.2 is enabled) | compliance.microsoft.com > Audit > Audit search |
| 15 | 8.1 | Document log review process: weekly review, 180-day retention | Governance document |
| 16 | 8.3 | Confirm 180-day retention meets IG1 requirements | compliance.microsoft.com > Audit > Retention |
| 17 | 13.1 | Configure M365 Defender alert notifications to IT Admin and Ops Manager | security.microsoft.com > Settings > Email notifications |

**Wave 3 outcome:** Visibility established. Security events can now be detected, investigated, and reviewed. Alert notifications ensure the team is aware of high-priority events.

---

### Wave 4 — Endpoint Management and Vulnerability (Month 2-3)

*Addresses: RISK-010 (Unpatched Endpoints), RISK-002 (Ransomware — backup). Cost: TTD 800-1,500/month for backup.*

| Order | Safeguard | Action | Admin Portal |
|-------|-----------|--------|-------------|
| 18 | 7.3 | Configure Windows Update rings in Intune (security updates within 7 days) | intune.microsoft.com > Devices > Update rings |
| 19 | 10.1 | Onboard endpoints to Defender for Business | security.microsoft.com > Settings > Endpoints > Onboarding |
| 20 | 10.2 | Verify cloud-delivered protection and auto-updates in Defender policy | intune.microsoft.com > Endpoint security > Antivirus |
| 21 | 10.3 | Disable autorun/autoplay via Intune configuration profile | intune.microsoft.com > Devices > Configuration profiles |
| 22 | 10.4 | Enable removable media scanning in Defender Antivirus policy | intune.microsoft.com > Endpoint security > Antivirus |
| 23 | 7.1 | Review Defender TVM dashboard; establish monthly review cadence | security.microsoft.com > Vulnerability management |
| 24 | 4.1 | Deploy Intune Security Baselines for Windows 11 and Edge | intune.microsoft.com > Endpoint security > Security baselines |
| 25 | 2.1 | Review Defender software inventory for all onboarded devices | security.microsoft.com > Asset management > Software inventory |
| 26 | 1.1 | Verify Intune device inventory; create supplementary list for unmanaged assets | intune.microsoft.com > Devices > All devices |
| 27 | 11.2 | Implement third-party M365 backup with immutable storage | Third-party vendor |
| 28 | 11.1 | Document RTO/RPO per system; verify EHR vendor backup SLA | Governance document + vendor engagement |
| 29 | 11.3 | Verify backup provider encryption and access controls | Third-party vendor |
| 30 | 11.4 | Confirm immutable/air-gapped backup storage is enabled | Third-party vendor |
| 31 | 3.9 | Enforce BitLocker To Go or block USB storage via Intune | intune.microsoft.com > Endpoint security > Disk encryption |
| 32 | 9.5 | Configure SPF, DKIM, and DMARC DNS records (start with p=none) | DNS provider + security.microsoft.com for verification |
| 33 | 3.3 | Configure SharePoint site permissions aligned to POL-002 access matrix | admin.microsoft.com > SharePoint admin center |
| 34 | 6.1 | Create Entra ID security groups per role; assign access via groups | entra.microsoft.com > Groups |
| 35 | 5.2 | Enable Entra ID Password Protection (banned password list) | entra.microsoft.com > Protection > Authentication methods |
| 36 | 7.2 | Establish monthly Defender remediation review process | security.microsoft.com > Vulnerability management > Remediation |
| 37 | 7.4 | Verify M365 Apps auto-update; identify third-party apps needing manual patching | admin.microsoft.com > Settings > Org settings |

**Wave 4 outcome:** Endpoints are managed, patched, and protected. Backup is in place. Email authentication is configured. Access management is formalized. Vulnerability management is operational.

---

### Wave 5 — Training and Governance (Month 4-6)

*Addresses: RISK-008 (No Training), RISK-019 (No Vendor Assessment). Cost: TTD 0 (using M365 built-in tools) to TTD 8,000 (if supplementing with third-party training).*

| Order | Safeguard | Action | Admin Portal |
|-------|-----------|--------|-------------|
| 38 | 14.1 | Launch M365 Attack Simulation Training platform | security.microsoft.com > Attack simulation training |
| 39 | 14.2 | Run first phishing simulation campaign targeting all staff | security.microsoft.com > Attack simulation training > Simulations |
| 40 | 14.3 | Deliver authentication training alongside MFA experience | Included in simulation training modules |
| 41 | 14.8 | Deploy Report Message add-in to all Outlook clients | admin.microsoft.com > Settings > Integrated apps |
| 42 | 17.7 | Conduct first tabletop exercise (BEC scenario) | Facilitated in-person |
| 43 | 3.2 | Configure Purview content explorer for M365 data discovery | compliance.microsoft.com > Data classification |
| 44 | 3.4 | Configure Purview retention policies per POL-004 | compliance.microsoft.com > Data lifecycle management |
| 45 | 3.7 | Create and publish Purview sensitivity labels matching POL-004 tiers | compliance.microsoft.com > Information protection |
| 46 | 3.12 | Create separate SharePoint sites with container-level sensitivity labels | admin.microsoft.com > SharePoint admin center |
| 47 | 15.1 | Review Entra ID enterprise apps; maintain full vendor register | entra.microsoft.com > Applications |
| 48 | 15.4 | Review and update vendor contracts per POL-005 | Governance activity |
| 49 | 14.4 | Create custom training content on MedCaribe data handling policies | Custom content development |
| 50 | 14.5 | Deliver unintentional data exposure training | Included in awareness program |
| 51 | 1.2 | Configure Conditional Access to require managed/compliant devices | entra.microsoft.com > Protection > Conditional Access |
| 52 | 2.2 | Review software inventory against vendor support lifecycles | Manual review using Defender inventory |
| 53 | 2.3 | Configure Intune app control for unauthorized software | intune.microsoft.com > Endpoint security > Application control |
| 54 | 3.5 | Configure Purview disposition review; establish physical disposal process | compliance.microsoft.com > Records management |
| 55 | 4.7 | Deploy Windows LAPS via Intune; change printer/NAS defaults manually | intune.microsoft.com > Endpoint security > Account protection |
| 56 | 17.6 | Establish Signal group as out-of-band IR communication channel | External to M365 |

---

### Wave 6 — Infrastructure Hardening (Month 7-12)

*Addresses: RISK-012 (Unsecured Network). Cost: TTD 5,000-15,000.*

| Order | Safeguard | Action |
|-------|-----------|--------|
| 57 | 12.1 | Replace consumer-grade routers with business-grade firewalls at primary locations |
| 58 | 12.6 | Implement network-level DNS filtering (Cloudflare Gateway or similar) |
| 59 | 9.2 | Enable Defender network protection on all managed endpoints |

**Wave 6 outcome:** Network infrastructure hardened. DNS filtering operational at network and endpoint level.

---

## 4. Milestone Summary

| Milestone | Timeline | Safeguards Completed | Cumulative Coverage |
|-----------|----------|---------------------|-------------------|
| Wave 1 complete | Week 1 | 6 | 25% (incl. pre-existing) |
| Wave 2 complete | Week 3 | 12 | 36% |
| Wave 3 complete | Week 4 | 17 | 48% |
| Wave 4 complete | Month 3 | 37 | 80% |
| Wave 5 complete | Month 6 | 56 | 96% |
| Wave 6 complete | Month 12 | 59 | 100% (incl. N/A) |

---

## 5. Document Control

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | March 2026 | J. Maitland | Initial implementation sequence |
