# CIS Controls v8 IG1 — M365 Coverage Report

**Document Classification:** Confidential — Executive Leadership  
**Version:** 1.0  
**Date:** March 2026  
**Prepared By:** Jelani D. Maitland  
**Audience:** Medical Director, Operations Manager

---

## Executive Summary

MedCaribe Health Group's existing Microsoft 365 Business Premium license includes security capabilities that can fully or partially address 46 of 56 CIS Controls v8 IG1 safeguards (82%). The remaining 8 safeguards (14%) require tools or processes outside of M365, and 2 (4%) are not applicable to MedCaribe's environment.

The most significant finding: **the majority of these capabilities are included in the current license but have never been configured.** MedCaribe is paying for enterprise-grade security tools and leaving them turned off.

---

## Coverage Breakdown

| Category | Safeguards | Percentage | What This Means |
|----------|-----------|------------|-----------------|
| Fully covered by M365 | 34 | 61% | Can be satisfied entirely through M365 configuration at no additional cost |
| Partially covered by M365 | 12 | 21% | M365 addresses part of the requirement; supplementary process or documentation needed |
| Not covered by M365 | 8 | 14% | Requires third-party tools, network infrastructure, or governance documents |
| Not applicable | 2 | 4% | Safeguard does not apply to MedCaribe (no in-house development or databases) |

---

## What M365 Does Well

**Identity and Access (Controls 5-6):** M365 provides comprehensive account management, MFA enforcement, Conditional Access, role-based access, and session management. This is the strongest coverage area and the single most impactful set of controls to implement.

**Email Security (Control 9):** Exchange Online Protection plus Defender for Office 365 provides anti-phishing, Safe Attachments (sandboxing), Safe Links, file type blocking, and DMARC support. Given that email compromise is MedCaribe's #1 risk, this coverage is critical.

**Malware Defenses (Control 10):** Defender for Business provides next-generation antivirus, cloud-delivered protection, endpoint detection and response, and centralized management. All four IG1 malware safeguards are fully covered.

**Audit Logging (Control 8):** Unified Audit Log captures events across all M365 services with 180-day retention. All four logging safeguards are fully addressable.

**Security Awareness (Control 14):** Attack Simulation Training provides phishing simulations and training modules. Five of six awareness safeguards are fully covered.

---

## Where M365 Falls Short

**Data Recovery (Control 11):** This is the critical gap. M365 does not provide true backup. Native retention features (versioning, recycle bin, deleted items recovery) are not substitutes for independent, immutable backup. Three of four data recovery safeguards require a third-party backup solution. **Estimated cost: TTD 800-1,500 per month.** This is the only significant recurring cost required.

**Network Infrastructure (Control 12):** M365 cannot manage routers, switches, access points, or network segmentation. MedCaribe's consumer-grade network equipment must be addressed through direct infrastructure investment. **Estimated cost: TTD 5,000-15,000 one-time for firewall deployment.**

**Service Provider Management (Control 15):** Vendor contracts and risk assessments are governance activities that M365 cannot automate. The Vendor Risk Policy (POL-005) from Project 1 provides the process framework.

**Incident Response (Control 17):** While M365 provides investigation tools and phishing simulations, the IR plan, team assignments, severity thresholds, and exercise facilitation are fundamentally human and process-driven. Project 1 deliverables satisfy these requirements.

---

## Investment Required Beyond M365

| Gap Area | Solution | Estimated Cost (TTD) | Priority |
|----------|----------|---------------------|----------|
| Data backup (Control 11) | Third-party M365 backup with immutable storage | 800-1,500/month | P2 — Month 2 |
| Network infrastructure (Control 12) | Business-grade firewalls, VLAN segmentation | 5,000-15,000 one-time | P4 — Month 7 |
| DNS filtering (Control 9/12) | Network-level DNS filtering service | 0-500/month | P4 — Month 8 |
| Password manager (Control 5) | Organization-wide password manager | 200-500/month | P2 — Month 2 |
| **Total additional Year 1** | | **TTD 16,000-36,000** | |

**Note:** The majority of CIS IG1 compliance (46 of 56 safeguards) requires zero additional spending beyond the existing M365 license.

---

## Recommended Actions for Leadership

1. **Authorize IT to configure M365 security features immediately.** 16 safeguards rated P1 (Immediate) can be addressed in Weeks 1-4 at zero cost. These include MFA enforcement, admin account separation, BitLocker encryption, audit logging, and email security policies.

2. **Approve the third-party backup investment.** Data recovery is the most critical gap. Without immutable backup, a ransomware attack could result in permanent loss of all M365 data. Budget: TTD 800-1,500/month.

3. **Schedule the security awareness training rollout for Month 4.** M365 includes Attack Simulation Training at no extra cost. The Operations Manager should plan the first phishing simulation campaign.

4. **Plan network infrastructure upgrades for Month 7-12.** This is the largest capital expenditure but is lower priority than identity, data protection, and backup.

---

## Document Control

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | March 2026 | J. Maitland | Initial coverage report |
