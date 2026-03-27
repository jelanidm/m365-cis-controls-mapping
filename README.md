# CIS Controls v8 IG1 — Microsoft 365 Implementation Mapping

## Mapping Essential Cyber Hygiene to Microsoft 365 Business Premium

**Framework:** CIS Critical Security Controls v8 — Implementation Group 1 (56 Safeguards)  
**Platform:** Microsoft 365 Business Premium (including Defender for Business and Intune)  
**Context:** MedCaribe Health Group — 55-person private healthcare provider, Trinidad and Tobago  
**Author:** Jelani D. Maitland  
**Date:** March 2026  
**Related Project:** [MedCaribe Security Program (Project 1)](https://github.com/jelani-maitland/medcaribe-security-program)

---

## Overview

This project maps every one of the 56 CIS Controls v8 Implementation Group 1 (IG1) safeguards to specific Microsoft 365 Business Premium features, settings, and capabilities. Each mapping identifies which M365 component satisfies the control, the admin portal path where the setting is configured, and the current implementation status for MedCaribe Health Group.

This is the companion to [Project 1 (MedCaribe Security Program)](https://github.com/jelani-maitland/medcaribe-security-program), which identified 20 cybersecurity risks and established governance documentation. This project answers the next question: "We know what our risks are. Now, how do we use the technology we already pay for to address them?"

---

## Why This Matters

Most small and midsize organizations already pay for Microsoft 365 Business Premium, which includes security capabilities that would cost tens of thousands of dollars separately: Intune for device management, Defender for Business for endpoint protection, Entra ID for identity management, and Exchange Online Protection for email security.

The problem is that most of these features are never configured. Organizations pay for enterprise-grade security tools and leave them turned off.

This mapping shows exactly which controls are already covered by the M365 license, which require only configuration (no additional cost), and which gaps remain that require supplementary tools or processes.

---

## Key Findings

Out of 56 IG1 safeguards:

- **34 safeguards (61%)** can be fully or substantially addressed using M365 Business Premium features
- **12 safeguards (21%)** are partially addressable through M365, with some gaps requiring process or documentation
- **10 safeguards (18%)** require capabilities outside of M365 (network infrastructure, physical security, or third-party tools)

**The single most impactful action:** Enforcing MFA across all accounts using Microsoft Entra ID. This single configuration change addresses parts of 6 different CIS safeguards and costs nothing beyond the existing license.

---

## Repository Structure

```
m365-cis-controls-mapping/
├── README.md
├── 01-mapping/
│   ├── cis-ig1-m365-mapping.md          # Full 56-safeguard mapping document
│   └── control-family-summary.md        # Summary by CIS control family (1-18)
├── 02-compliance-tracker/
│   └── implementation-tracker.md        # Status, priority, effort, owner per safeguard
├── 03-executive-summary/
│   ├── coverage-report.md               # What M365 covers vs. gaps
│   └── implementation-sequence.md       # Recommended rollout order for MedCaribe
└── pdf-versions/
    └── (all documents exported as PDF)
```

---

## M365 Business Premium Components Referenced

| Component | Purpose | Admin Portal |
|-----------|---------|-------------|
| Microsoft Entra ID | Identity and access management, MFA, Conditional Access | entra.microsoft.com |
| Exchange Online Protection | Email filtering, anti-phishing, anti-malware, mail flow rules | security.microsoft.com |
| Microsoft Defender for Business | Endpoint detection and response, vulnerability management | security.microsoft.com |
| Microsoft Intune | Device management, compliance policies, app management, patching | intune.microsoft.com |
| Microsoft Purview | Data classification, sensitivity labels, DLP (basic) | compliance.microsoft.com |
| OneDrive / SharePoint | File storage, sharing controls, versioning | admin.microsoft.com |
| Microsoft 365 Audit Log | Unified audit logging for all M365 services | compliance.microsoft.com |

---

## How to Use This Repository

**If you are implementing M365 security for a small organization:** Start with the implementation tracker. It shows which safeguards to configure first based on risk impact and effort. Follow the recommended sequence in the executive summary.

**If you are a GRC professional:** Use the mapping document to demonstrate how M365 satisfies specific CIS Controls requirements. This is directly useful for compliance evidence collection and audit preparation.

**If you are studying for CySA+, Security+, or SC-200:** Walk through the mapping to understand how governance frameworks translate to real-world platform configurations. This bridges the gap between exam knowledge and practical implementation.

---

## About the Author

Jelani D. Maitland is a cybersecurity professional based in Trinidad and Tobago, holding CySA+, Security+, SC-200, and Fortinet FCA certifications. He specializes in security operations, governance, and risk management for small and midsize organizations in the Caribbean.

- [LinkedIn](https://linkedin.com/in/jelani-maitland)
- [GitHub](https://github.com/jelani-maitland)

---

## License

This project is shared under the [MIT License](LICENSE). You are free to use, modify, and distribute these materials with attribution.
