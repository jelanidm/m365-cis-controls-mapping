# CIS Controls v8 IG1 - Microsoft 365 Business Premium Mapping

**Document Classification:** Internal - Security Program  
**Version:** 1.0  
**Date:** March 2026  
**Author:** Jelani D. Maitland  
**Context:** MedCaribe Health Group  
**Review Cycle:** Annual or upon significant M365 licensing or feature changes

---

## 1. Purpose

This document maps each of the 56 CIS Controls v8 Implementation Group 1 (IG1) safeguards to the corresponding Microsoft 365 Business Premium feature or capability that can satisfy it. Where M365 cannot fully address a safeguard, the gap is identified and an alternative approach is noted.

---

## 2. How to Read This Document

Each safeguard entry includes:

- **Safeguard ID and Title:** The official CIS designation
- **What It Requires:** Plain-language description of the safeguard
- **M365 Feature:** The specific M365 component that addresses it
- **Admin Portal Path:** Where to find and configure the relevant setting
- **M365 Coverage:** Full, Partial, or None
- **MedCaribe Status:** Current implementation state at MedCaribe Health Group
- **Notes:** Additional context, gaps, or recommendations

**Coverage definitions:** Full = M365 can fully satisfy this safeguard with configuration. Partial = M365 addresses part of the safeguard but gaps remain. None = M365 does not address this safeguard; requires external tools or processes.

---

## 3. Control 1 - Inventory and Control of Enterprise Assets

*Purpose: Actively manage all enterprise assets connected to the infrastructure.*

### 1.1 - Establish and Maintain Detailed Enterprise Asset Inventory

| Field | Detail |
|-------|--------|
| **What It Requires** | Maintain a detailed inventory of all assets that can store or process data, including end-user devices, network devices, IoT, and servers. Record network address, hardware address, machine name, owner, department, and network approval status. |
| **M365 Feature** | Microsoft Intune (device inventory), Microsoft Entra ID (registered/joined devices) |
| **Admin Portal Path** | Intune: intune.microsoft.com > Devices > All devices. Entra ID: entra.microsoft.com > Devices > All devices |
| **M365 Coverage** | Partial |
| **MedCaribe Status** | Not Implemented |
| **Notes** | M365 covers enrolled endpoints (workstations, laptops, mobile devices) but does not inventory network devices (routers, switches, access points), printers, or IoT devices. A supplementary spreadsheet or CMDB is needed for non-enrolled assets. |

### 1.2 - Address Unauthorized Assets

| Field | Detail |
|-------|--------|
| **What It Requires** | Ensure a process exists to address unauthorized assets on a weekly basis. Remove, deny network access, or quarantine unauthorized assets. |
| **M365 Feature** | Intune Compliance Policies (block non-compliant devices), Entra ID Conditional Access (require managed device) |
| **Admin Portal Path** | Intune: intune.microsoft.com > Devices > Compliance policies. Entra ID: entra.microsoft.com > Protection > Conditional Access |
| **M365 Coverage** | Partial |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Conditional Access can block unmanaged devices from accessing M365 services. However, this does not control network-level access (requires network infrastructure controls). |

---

## 4. Control 2 - Inventory and Control of Software Assets

*Purpose: Actively manage all software to ensure only authorized software is installed.*

### 2.1 - Establish and Maintain a Software Inventory

| Field | Detail |
|-------|--------|
| **What It Requires** | Maintain a detailed inventory of all licensed software, including title, publisher, install date, business purpose, URL, version, and deployment mechanism. |
| **M365 Feature** | Intune (discovered apps, managed apps), Defender for Business (software inventory) |
| **Admin Portal Path** | Intune: intune.microsoft.com > Apps > Monitor > Discovered apps. Defender: security.microsoft.com > Asset management > Device inventory > Software tab |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Defender for Business provides automatic software discovery on onboarded endpoints. Combined with Intune app management, this creates a comprehensive software inventory for managed devices. |

### 2.2 - Ensure Authorized Software is Currently Supported

| Field | Detail |
|-------|--------|
| **What It Requires** | Ensure only currently supported software is designated as authorized. Unsupported software must be designated unauthorized and documented if an exception is required. |
| **M365 Feature** | Defender for Business (software inventory with version tracking), Intune (app deployment) |
| **Admin Portal Path** | Defender: security.microsoft.com > Asset management > Device inventory > Software vulnerabilities |
| **M365 Coverage** | Partial |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Defender identifies software versions and known vulnerabilities but does not automatically flag end-of-support status. Manual review of the software list against vendor support lifecycles is still needed. |

### 2.3 - Address Unauthorized Software

| Field | Detail |
|-------|--------|
| **What It Requires** | Ensure a process exists to address unauthorized software, either by removing, disabling, or documenting an exception. Review monthly or more frequently. |
| **M365 Feature** | Intune (app control policies, Windows Defender Application Control) |
| **Admin Portal Path** | Intune: intune.microsoft.com > Endpoint security > Application control |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Intune can restrict app installation to approved applications. For a simpler approach, configure Windows Defender SmartScreen to block unrecognized apps and educate staff on the approval process. |

---

## 5. Control 3 - Data Protection

*Purpose: Develop processes and technical controls to identify, classify, securely handle, retain, and dispose of data.*

### 3.1 - Establish and Maintain a Data Management Process

| Field | Detail |
|-------|--------|
| **What It Requires** | Document a data management process addressing sensitivity, ownership, handling, retention, and disposal. Review annually. |
| **M365 Feature** | Microsoft Purview (data lifecycle management, retention policies) |
| **Admin Portal Path** | Purview: compliance.microsoft.com > Data lifecycle management > Retention policies |
| **M365 Coverage** | Partial |
| **MedCaribe Status** | Not Implemented - Data Classification Policy created in Project 1 but not yet implemented in M365 |
| **Notes** | M365 provides the technical enforcement layer (retention labels, policies) but the documented process itself is a governance deliverable. Project 1's Data Classification Policy (POL-004) satisfies the documentation requirement. |

### 3.2 - Establish and Maintain a Data Inventory

| Field | Detail |
|-------|--------|
| **What It Requires** | Inventory sensitive data at minimum. Review and update annually. |
| **M365 Feature** | Microsoft Purview (Content Explorer, Activity Explorer, Data Classification dashboard) |
| **Admin Portal Path** | Purview: compliance.microsoft.com > Data classification > Content explorer |
| **M365 Coverage** | Partial |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Purview can discover and classify sensitive data across M365 (email, OneDrive, SharePoint) using built-in sensitive information types. Does not cover data in third-party SaaS (CloudMed EHR, QuickBooks). |

### 3.3 - Configure Data Access Control Lists

| Field | Detail |
|-------|--------|
| **What It Requires** | Configure access controls based on need-to-know. Apply to local and remote file systems, databases, and applications. |
| **M365 Feature** | SharePoint/OneDrive permissions, Entra ID groups, Sensitivity labels with access restrictions |
| **Admin Portal Path** | SharePoint: admin.microsoft.com > SharePoint admin center > Sites > Permissions. Entra ID: entra.microsoft.com > Groups |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | SharePoint site-level permissions combined with Entra ID security groups provide granular access control. Sensitivity labels can automatically restrict access based on data classification. |

### 3.4 - Enforce Data Retention

| Field | Detail |
|-------|--------|
| **What It Requires** | Retain data per the documented data management process. |
| **M365 Feature** | Microsoft Purview (retention policies, retention labels) |
| **Admin Portal Path** | Purview: compliance.microsoft.com > Data lifecycle management > Retention policies |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Retention policies can be applied to Exchange email, OneDrive, SharePoint, and Teams. Can enforce minimum retention periods (e.g., 7 years for patient-related email) and auto-delete after expiry. |

### 3.5 - Securely Dispose of Data

| Field | Detail |
|-------|--------|
| **What It Requires** | Securely dispose of data per the data management process. |
| **M365 Feature** | Microsoft Purview (disposition review, retention label auto-delete), Intune (remote wipe) |
| **Admin Portal Path** | Purview: compliance.microsoft.com > Records management > Disposition. Intune: intune.microsoft.com > Devices > [device] > Wipe |
| **M365 Coverage** | Partial |
| **MedCaribe Status** | Not Implemented |
| **Notes** | M365 handles digital disposal for data within the platform. Physical media disposal and third-party system data disposal require separate processes. Intune can remotely wipe departing employee devices. |

### 3.6 - Encrypt Data on End-User Devices

| Field | Detail |
|-------|--------|
| **What It Requires** | Encrypt data on end-user devices including portable and mobile devices. |
| **M365 Feature** | Intune (BitLocker policy for Windows, FileVault for Mac), built-in iOS/Android encryption |
| **Admin Portal Path** | Intune: intune.microsoft.com > Endpoint security > Disk encryption |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented - identified as Phase 1 Quick Win in Project 1 |
| **Notes** | Intune can enforce BitLocker on all Windows 11 Pro devices with recovery key escrow to Entra ID. All modern iOS and Android devices encrypt by default when a passcode is set. |

### 3.7 - Establish and Maintain a Data Classification Scheme

| Field | Detail |
|-------|--------|
| **What It Requires** | Maintain an overall classification scheme (e.g., Sensitive, Confidential, Public). Review annually. |
| **M365 Feature** | Microsoft Purview (sensitivity labels, label policies) |
| **Admin Portal Path** | Purview: compliance.microsoft.com > Information protection > Labels |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Governance document created (Project 1 POL-004) but not technically enforced in M365 |
| **Notes** | Purview sensitivity labels can be published to users for manual labelling of documents and emails. Auto-labelling policies can classify data automatically based on content. Maps directly to the four-tier scheme in POL-004 (Public, Internal, Confidential, Restricted). |

### 3.9 - Encrypt Data on Removable Media

| Field | Detail |
|-------|--------|
| **What It Requires** | Encrypt data on removable media. |
| **M365 Feature** | Intune (device control policies, BitLocker To Go enforcement) |
| **Admin Portal Path** | Intune: intune.microsoft.com > Endpoint security > Disk encryption (BitLocker To Go settings) |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Intune can enforce BitLocker To Go for USB drives, requiring encryption before data can be written. Can also block USB storage entirely via device control policies. |

### 3.10 - Encrypt Sensitive Data in Transit

| Field | Detail |
|-------|--------|
| **What It Requires** | Encrypt sensitive data in transit using TLS, OpenSSH, or equivalent. |
| **M365 Feature** | Exchange Online (TLS enforcement), SharePoint/OneDrive (HTTPS by default), Microsoft 365 Message Encryption |
| **Admin Portal Path** | Exchange: admin.exchange.microsoft.com > Mail flow > Connectors (TLS settings). Security: security.microsoft.com > Email & collaboration > Policies |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Partial - M365 enforces TLS by default for supported recipients; not explicitly configured or verified |
| **Notes** | M365 enforces TLS 1.2 by default for all services. Exchange Online opportunistic TLS encrypts email in transit when the receiving server supports it. M365 Message Encryption can be used for sensitive email requiring guaranteed encryption. |

### 3.11 - Encrypt Sensitive Data at Rest

| Field | Detail |
|-------|--------|
| **What It Requires** | Encrypt sensitive data at rest on servers, applications, and databases. |
| **M365 Feature** | Microsoft manages encryption at rest for all M365 data (BitLocker at data centre level, service encryption with Customer Key available) |
| **Admin Portal Path** | N/A - enabled by default; Customer Key available in compliance.microsoft.com for organizations requiring key management |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Implemented (by default) - M365 encrypts all data at rest natively |
| **Notes** | All data stored in Exchange Online, SharePoint, OneDrive, and Teams is encrypted at rest by default using AES-256. No action required for basic compliance. |

### 3.12 - Segment Data Processing and Storage Based on Sensitivity

| Field | Detail |
|-------|--------|
| **What It Requires** | Segment data processing and storage based on the sensitivity of the data. |
| **M365 Feature** | SharePoint sites with different permission levels, sensitivity labels with container-level protection, Entra ID security groups |
| **Admin Portal Path** | SharePoint admin center > Sites > Create site with specific access. Purview: compliance.microsoft.com > Information protection > Label policies |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Create separate SharePoint sites for different sensitivity levels (e.g., "Clinical Documents" restricted to clinical staff, "General" open to all staff). Apply container-level sensitivity labels to restrict access, sharing, and guest permissions by site. |

---

## 6. Control 4 - Secure Configuration of Enterprise Assets and Software

*Purpose: Establish and maintain secure configurations for enterprise assets and software.*

### 4.1 - Establish and Maintain a Secure Configuration Process

| Field | Detail |
|-------|--------|
| **What It Requires** | Establish and maintain a documented secure configuration process for enterprise assets and software. Review annually. |
| **M365 Feature** | Intune (Security Baselines, Configuration Profiles), Defender for Business (security recommendations) |
| **Admin Portal Path** | Intune: intune.microsoft.com > Endpoint security > Security baselines. Defender: security.microsoft.com > Secure score > Recommended actions |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Microsoft provides pre-built security baselines for Windows, Edge, and Defender that can be deployed through Intune. Microsoft Secure Score provides ongoing configuration recommendations. |

### 4.3 - Configure Automatic Session Locking on Enterprise Assets

| Field | Detail |
|-------|--------|
| **What It Requires** | Configure automatic session locking after a period of inactivity. Set to 15 minutes or less. |
| **M365 Feature** | Intune (device configuration profile - screen lock timeout) |
| **Admin Portal Path** | Intune: intune.microsoft.com > Devices > Configuration profiles > Create > Settings catalog > "Screen lock" |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented - Project 1 Access Control Policy specifies 10-minute timeout |
| **Notes** | Intune can enforce screen lock timeout on Windows, iOS, and Android devices. MedCaribe's Access Control Policy (POL-002) specifies 10 minutes, which is stricter than the CIS minimum of 15. |

### 4.7 - Manage Default Accounts on Enterprise Assets and Software

| Field | Detail |
|-------|--------|
| **What It Requires** | Manage default accounts on enterprise assets and software. Change defaults, disable if possible, or document risk. |
| **M365 Feature** | Entra ID (rename/disable default admin account is not applicable - cloud identity), Intune (local admin password solution - LAPS) |
| **Admin Portal Path** | Entra ID: entra.microsoft.com > Users > User settings. Intune: intune.microsoft.com > Endpoint security > Account protection > Local admin password solution |
| **M365 Coverage** | Partial |
| **MedCaribe Status** | Not Implemented |
| **Notes** | M365 cloud accounts don't have traditional "default accounts," but Windows LAPS via Intune manages local administrator passwords on endpoints. Printers, routers, and NAS devices with default credentials are outside M365 scope and must be addressed manually. |

---

## 7. Control 5 - Account Management

*Purpose: Use processes and tools to assign and manage authorization to credentials for user accounts.*

### 5.1 - Establish and Maintain an Inventory of Accounts

| Field | Detail |
|-------|--------|
| **What It Requires** | Maintain an inventory of all accounts, including user, administrator, and service accounts. Include username, department, start/stop dates, and authorized privileges. |
| **M365 Feature** | Entra ID (user list with role assignments, sign-in activity), Intune (user inventory) |
| **Admin Portal Path** | Entra ID: entra.microsoft.com > Users > All users (export to CSV available) |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Partial - accounts exist in Entra ID but no formal inventory review process |
| **Notes** | Entra ID maintains the definitive account list. Export regularly for review. Filter by "account enabled" status and "last sign-in" to identify dormant accounts. |

### 5.2 - Use Unique Passwords

| Field | Detail |
|-------|--------|
| **What It Requires** | Use unique passwords for all enterprise assets. Best practice is to use a password manager. |
| **M365 Feature** | Entra ID (password policies, banned password list), Entra ID Password Protection |
| **Admin Portal Path** | Entra ID: entra.microsoft.com > Protection > Authentication methods > Password protection |
| **M365 Coverage** | Partial |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Entra ID enforces password complexity and can block common/leaked passwords. However, it cannot enforce unique passwords across non-M365 systems (EHR, QuickBooks, insurance portals). A password manager recommendation should accompany this control. |

### 5.3 - Disable Dormant Accounts

| Field | Detail |
|-------|--------|
| **What It Requires** | Delete or disable dormant accounts after 45 days of inactivity. |
| **M365 Feature** | Entra ID (sign-in logs with last activity date), Entra ID Access Reviews |
| **Admin Portal Path** | Entra ID: entra.microsoft.com > Users > All users > filter by "Last sign-in" |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented - no offboarding process existed prior to Project 1 |
| **Notes** | Filter Entra ID users by last sign-in date to identify accounts inactive for 45+ days. Disable and investigate. Align with offboarding checklist from Project 1. |

### 5.4 - Restrict Administrator Privileges to Dedicated Administrator Accounts

| Field | Detail |
|-------|--------|
| **What It Requires** | Restrict admin privileges to dedicated admin accounts. Admin accounts must not be used for daily tasks like email and web browsing. |
| **M365 Feature** | Entra ID (create separate admin accounts, assign admin roles only to dedicated accounts) |
| **Admin Portal Path** | Entra ID: entra.microsoft.com > Roles and administrators |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented - identified as Phase 1 Quick Win in Project 1 |
| **Notes** | Create admin.[username]@medcaribe.tt accounts for IT administration. Remove Global Admin and other admin roles from daily-use accounts. This is a zero-cost configuration change. |

---

## 8. Control 6 - Access Management

*Purpose: Use processes and tools to create, assign, manage, and revoke access credentials and privileges.*

### 6.1 - Establish an Access Granting Process

| Field | Detail |
|-------|--------|
| **What It Requires** | Establish and follow a process to grant access based on documented need. |
| **M365 Feature** | Entra ID (role assignments, group-based access), SharePoint (site permissions) |
| **Admin Portal Path** | Entra ID: entra.microsoft.com > Users > [user] > Assigned roles. Groups: entra.microsoft.com > Groups |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented - Access Control Policy (POL-002) defines the process; technical enforcement pending |
| **Notes** | Use Entra ID security groups aligned to the role-based access matrix in POL-002. Assign M365 licenses, app access, and SharePoint permissions via groups rather than individual assignments. |

### 6.2 - Establish an Access Revoking Process

| Field | Detail |
|-------|--------|
| **What It Requires** | Establish and follow a process to revoke access upon termination, rights reduction, or role change. |
| **M365 Feature** | Entra ID (disable account, revoke sessions, remove group memberships), Intune (remote wipe) |
| **Admin Portal Path** | Entra ID: entra.microsoft.com > Users > [user] > Block sign-in / Revoke sessions |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented - offboarding checklist created in Project 1 |
| **Notes** | Blocking sign-in in Entra ID immediately prevents access to all M365 services. "Revoke sessions" forces sign-out from all active sessions. Intune can remotely wipe managed devices. |

### 6.3 - Require MFA for Externally-Exposed Applications

| Field | Detail |
|-------|--------|
| **What It Requires** | Require MFA for all externally-exposed enterprise or third-party applications. |
| **M365 Feature** | Entra ID (Security Defaults or Conditional Access policies) |
| **Admin Portal Path** | Entra ID: entra.microsoft.com > Protection > Conditional Access > New policy (or entra.microsoft.com > Overview > Properties > Security defaults) |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Partial - MFA enabled for management accounts only |
| **Notes** | Enable Security Defaults (simplest approach) to enforce MFA for all users, or create a Conditional Access policy for more granular control. M365 Business Premium includes Conditional Access. This is the single highest-impact control in the entire IG1 set. |

### 6.4 - Require MFA for Remote Network Access

| Field | Detail |
|-------|--------|
| **What It Requires** | Require MFA for all remote network access. |
| **M365 Feature** | Entra ID (Conditional Access - require MFA for all locations or non-trusted locations) |
| **Admin Portal Path** | Entra ID: entra.microsoft.com > Protection > Conditional Access > Named locations + policies |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | For a cloud-first organization like MedCaribe, all access is effectively remote. Conditional Access can require MFA for all sign-ins, or exempt trusted office IPs while requiring MFA from other locations. |

### 6.5 - Require MFA for Administrative Access

| Field | Detail |
|-------|--------|
| **What It Requires** | Require MFA for all administrative access to enterprise assets. |
| **M365 Feature** | Entra ID (Conditional Access - require MFA for admin roles), Security Defaults (MFA for admins by default) |
| **Admin Portal Path** | Entra ID: entra.microsoft.com > Protection > Conditional Access > New policy > Target: Directory roles |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Partial - MFA on some admin accounts but not enforced via policy |
| **Notes** | Create a dedicated Conditional Access policy that requires MFA for all accounts assigned admin roles. Consider requiring phishing-resistant MFA (FIDO2 or certificate-based) for admin accounts where feasible. |

---

## 9. Control 7 - Continuous Vulnerability Management

*Purpose: Develop a plan to continuously assess and track vulnerabilities on all enterprise assets.*

### 7.1 - Establish and Maintain a Vulnerability Management Process

| Field | Detail |
|-------|--------|
| **What It Requires** | Establish and maintain a documented vulnerability management process for enterprise assets. Review and update annually. |
| **M365 Feature** | Defender for Business (Vulnerability Management dashboard, security recommendations) |
| **Admin Portal Path** | Defender: security.microsoft.com > Vulnerability management > Dashboard |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Defender for Business includes Threat and Vulnerability Management (TVM) which automatically identifies vulnerabilities on onboarded endpoints and provides prioritized remediation recommendations. |

### 7.2 - Establish and Maintain a Remediation Process

| Field | Detail |
|-------|--------|
| **What It Requires** | Establish and maintain a risk-based remediation strategy with monthly or more frequent review. |
| **M365 Feature** | Defender for Business (remediation requests, security recommendations with priority scoring) |
| **Admin Portal Path** | Defender: security.microsoft.com > Vulnerability management > Remediation |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Defender for Business provides exposure scores and prioritized remediation tasks. Remediation requests can be tracked and assigned. |

### 7.3 - Perform Automated Operating System Patch Management

| Field | Detail |
|-------|--------|
| **What It Requires** | Perform automated operating system patch management monthly or more frequently. |
| **M365 Feature** | Intune (Windows Update for Business, update rings), Defender for Business (patch recommendations) |
| **Admin Portal Path** | Intune: intune.microsoft.com > Devices > Windows > Update rings for Windows 10 and later |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented - identified as Phase 2 action in Project 1 |
| **Notes** | Configure Windows Update rings in Intune to automatically deploy security updates within 7 days of release. Deferral periods can be set for feature updates. |

### 7.4 - Perform Automated Application Patch Management

| Field | Detail |
|-------|--------|
| **What It Requires** | Perform automated application patch management monthly or more frequently. |
| **M365 Feature** | Intune (app deployment and updates for managed apps), Microsoft 365 Apps auto-update |
| **Admin Portal Path** | Intune: intune.microsoft.com > Apps > All apps. M365 Apps: admin.microsoft.com > Settings > Org settings > Microsoft 365 installation options |
| **M365 Coverage** | Partial |
| **MedCaribe Status** | Not Implemented |
| **Notes** | M365 Apps (Word, Excel, Outlook, etc.) auto-update by default. Intune can deploy and update additional managed apps. Third-party applications not managed through Intune require manual patching or a third-party patch management solution. |

---

## 10. Control 8 - Audit Log Management

*Purpose: Collect, alert, review, and retain audit logs of events that could help detect, understand, or recover from an attack.*

### 8.1 - Establish and Maintain an Audit Log Management Process

| Field | Detail |
|-------|--------|
| **What It Requires** | Establish and maintain an audit log management process that defines logging requirements, review frequency, and retention. Review annually. |
| **M365 Feature** | Microsoft 365 Unified Audit Log, Microsoft Purview Audit |
| **Admin Portal Path** | Purview: compliance.microsoft.com > Audit > Audit search. Admin: admin.microsoft.com > Settings > Org settings > Audit |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented - audit logging available but never enabled or reviewed |
| **Notes** | M365 Unified Audit Log captures events across Exchange, SharePoint, OneDrive, Teams, Entra ID, and more. Must be explicitly turned on for some tenants. Default retention is 180 days (Business Premium); Audit Premium extends to 1 year. |

### 8.2 - Collect Audit Logs

| Field | Detail |
|-------|--------|
| **What It Requires** | Collect audit logs from enterprise assets. Ensure logging is enabled on all relevant systems. |
| **M365 Feature** | M365 Unified Audit Log (all M365 services), Entra ID Sign-in Logs, Defender for Business (device timeline) |
| **Admin Portal Path** | Purview: compliance.microsoft.com > Audit. Entra ID: entra.microsoft.com > Monitoring > Sign-in logs |
| **M365 Coverage** | Full (for M365-managed assets) |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Covers all M365 services and enrolled endpoints. Network devices, printers, and third-party SaaS (EHR, QuickBooks) generate their own logs outside M365 scope. |

### 8.3 - Ensure Adequate Audit Log Storage

| Field | Detail |
|-------|--------|
| **What It Requires** | Ensure log storage is adequate for compliance and review requirements. |
| **M365 Feature** | M365 Audit Log (180 days default for Business Premium, 1 year with Audit Premium add-on) |
| **Admin Portal Path** | Purview: compliance.microsoft.com > Audit > Audit retention policies |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | 180-day retention with Business Premium is adequate for IG1 baseline requirements. For extended retention (e.g., 1 year per MedCaribe Data Classification Policy), evaluate the Audit Premium add-on or export logs to external storage. |

### 8.5 - Collect Detailed Audit Logs

| Field | Detail |
|-------|--------|
| **What It Requires** | Configure detailed audit logging to include event source, date, username, timestamp, source/destination addresses, and other useful elements. |
| **M365 Feature** | M365 Unified Audit Log (detailed event logging is built-in when enabled) |
| **Admin Portal Path** | Purview: compliance.microsoft.com > Audit |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | M365 audit logs natively capture user, timestamp, IP address, action, target object, and result for all logged events. No additional configuration needed beyond enabling the audit log. |

---

## 11. Control 9 - Email and Web Browser Protections

*Purpose: Improve protections and detections of threats from email and web vectors.*

### 9.2 - Use DNS Filtering Services

| Field | Detail |
|-------|--------|
| **What It Requires** | Use DNS filtering services on all enterprise assets to block access to known malicious domains. |
| **M365 Feature** | Defender for Business (web content filtering, network protection) |
| **Admin Portal Path** | Defender: security.microsoft.com > Settings > Endpoints > Web content filtering |
| **M365 Coverage** | Partial |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Defender for Business provides web content filtering on managed endpoints but this is not true DNS-level filtering for the entire network. For network-wide DNS filtering, a service like Cloudflare Gateway or Cisco Umbrella is needed at the router level. |

### 9.5 - Implement DMARC

| Field | Detail |
|-------|--------|
| **What It Requires** | Implement DMARC to lower the chance of spoofed or modified emails from valid domains. Start with a monitoring-only policy. |
| **M365 Feature** | Exchange Online (DMARC, DKIM, SPF configuration through DNS) |
| **Admin Portal Path** | DNS provider (not M365 admin center) - configure TXT records for SPF, DKIM, and DMARC. Verify at: security.microsoft.com > Email & collaboration > Policies > Threat policies > Email authentication |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | SPF, DKIM, and DMARC are DNS-based configurations that work with Exchange Online. Start with a DMARC policy of p=none (monitoring) to collect reports, then escalate to p=quarantine and eventually p=reject. M365 provides built-in DKIM signing for custom domains. |

### 9.6 - Block Unnecessary File Types

| Field | Detail |
|-------|--------|
| **What It Requires** | Block unnecessary file types from entering the enterprise's email gateway. |
| **M365 Feature** | Exchange Online Protection (anti-malware policy - common attachment types filter) |
| **Admin Portal Path** | Security: security.microsoft.com > Email & collaboration > Policies > Threat policies > Anti-malware > Edit default policy > Common attachments filter |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Enable the common attachments filter to block executable file types (.exe, .bat, .cmd, .js, .vbs, etc.) in email. Customize the blocked file type list based on business requirements. |

### 9.7 - Deploy and Maintain Email Server Anti-Malware Protections

| Field | Detail |
|-------|--------|
| **What It Requires** | Deploy and maintain email server anti-malware protections such as attachment scanning and sandboxing. |
| **M365 Feature** | Exchange Online Protection (anti-malware), Defender for Office 365 Plan 1 (Safe Attachments - sandboxing) |
| **Admin Portal Path** | Security: security.microsoft.com > Email & collaboration > Policies > Threat policies > Safe Attachments |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Exchange Online Protection provides baseline anti-malware scanning for all email. Defender for Office 365 (included in Business Premium) adds Safe Attachments which detonates suspicious attachments in a sandbox before delivery. |

---

## 12. Control 10 - Malware Defenses

*Purpose: Prevent or control the installation, spread, and execution of malicious applications, code, or scripts.*

### 10.1 - Deploy and Maintain Anti-Malware Software

| Field | Detail |
|-------|--------|
| **What It Requires** | Deploy and maintain anti-malware software on all enterprise assets. |
| **M365 Feature** | Defender for Business (next-generation antivirus, EDR), Microsoft Defender Antivirus (built into Windows) |
| **Admin Portal Path** | Defender: security.microsoft.com > Settings > Endpoints > Onboarding. Intune: intune.microsoft.com > Endpoint security > Antivirus |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Partial - Defender Antivirus exists on Windows devices but Defender for Business is not onboarded |
| **Notes** | Microsoft Defender Antivirus is built into Windows 11. Defender for Business (included in M365 Business Premium) adds cloud-delivered protection, EDR capabilities, and centralized management. Must be onboarded via Intune or local script. |

### 10.2 - Configure Automatic Anti-Malware Signature Updates

| Field | Detail |
|-------|--------|
| **What It Requires** | Configure automatic updates for anti-malware signature files on all enterprise assets. |
| **M365 Feature** | Defender for Business (cloud-delivered protection, automatic signature updates) |
| **Admin Portal Path** | Intune: intune.microsoft.com > Endpoint security > Antivirus > Create policy > Defender Antivirus > Cloud-delivered protection |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Partial - Windows Defender updates automatically by default but not centrally managed |
| **Notes** | Defender Antivirus updates automatically via Windows Update. Cloud-delivered protection provides near-real-time signature updates. Enable and verify cloud-delivered protection level via Intune policy. |

### 10.3 - Disable Autorun and Autoplay for Removable Media

| Field | Detail |
|-------|--------|
| **What It Requires** | Disable autorun and autoplay auto-execute functionality for removable media. |
| **M365 Feature** | Intune (device configuration profile - Windows settings) |
| **Admin Portal Path** | Intune: intune.microsoft.com > Devices > Configuration profiles > Settings catalog > "AutoPlay" |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Configure Intune device configuration profile to disable AutoPlay and AutoRun for all removable media types. This is a one-time configuration change. |

### 10.4 - Configure Automatic Anti-Malware Scanning of Removable Media

| Field | Detail |
|-------|--------|
| **What It Requires** | Configure anti-malware to automatically scan removable media. |
| **M365 Feature** | Defender for Business / Defender Antivirus (scan removable drives) |
| **Admin Portal Path** | Intune: intune.microsoft.com > Endpoint security > Antivirus > Create policy > Scan removable drives |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Enable "Scan removable drives during full scan" in Defender Antivirus policy via Intune. Real-time protection also monitors files opened from removable media. |

---

## 13. Control 11 - Data Recovery

*Purpose: Establish and maintain data recovery practices sufficient to restore in-scope enterprise assets to a pre-incident and trusted state.*

### 11.1 - Establish and Maintain a Data Recovery Practice

| Field | Detail |
|-------|--------|
| **What It Requires** | Establish and maintain a documented data recovery practice including scope, RTO, RPO, and test schedule. |
| **M365 Feature** | M365 native retention and versioning (OneDrive, SharePoint, Exchange), third-party backup recommended |
| **Admin Portal Path** | OneDrive: admin.microsoft.com > SharePoint admin center > Settings > OneDrive > Retention. Exchange: admin.exchange.microsoft.com > Mailboxes > [user] > Retention |
| **M365 Coverage** | Partial |
| **MedCaribe Status** | Not Implemented |
| **Notes** | M365 provides versioning (OneDrive/SharePoint) and deleted item recovery (Exchange) but these are retention features, not true backup. A third-party M365 backup solution (e.g., Veeam, Datto, AvePoint) is strongly recommended for immutable backup with granular restore. |

### 11.2 - Perform Automated Backups

| Field | Detail |
|-------|--------|
| **What It Requires** | Perform automated backups of in-scope enterprise assets at least weekly or more frequently for sensitive data. |
| **M365 Feature** | Third-party M365 backup required (native M365 does not provide automated independent backup) |
| **Admin Portal Path** | N/A - requires third-party backup solution |
| **M365 Coverage** | None (native); Full with third-party add-on |
| **MedCaribe Status** | Not Implemented - identified as Phase 2 priority in Project 1 |
| **Notes** | This is a critical gap. M365's native capabilities (versioning, retention) do not constitute backup. Implement a third-party solution for Exchange, OneDrive, SharePoint, and Teams. Budget: approx. TTD 800-1,500/month. |

### 11.3 - Protect Recovery Data

| Field | Detail |
|-------|--------|
| **What It Requires** | Protect recovery data with equivalent controls as the original data. Encrypt backup data. |
| **M365 Feature** | Third-party backup solution (encryption, access controls) |
| **Admin Portal Path** | N/A - third-party dependent |
| **M365 Coverage** | None (native); depends on backup solution |
| **MedCaribe Status** | Not Implemented |
| **Notes** | When selecting a third-party backup provider, verify encryption at rest and in transit, RBAC for backup access, and data residency compliance for the TT Data Protection Act. |

### 11.4 - Establish and Maintain an Isolated Instance of Recovery Data

| Field | Detail |
|-------|--------|
| **What It Requires** | Maintain at least one isolated (air-gapped or immutable) backup copy. |
| **M365 Feature** | Third-party backup with immutable storage |
| **Admin Portal Path** | N/A - third-party dependent |
| **M365 Coverage** | None |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Critical for ransomware protection. The backup copy must be immutable (cannot be modified or deleted even by an admin) or air-gapped. Most cloud backup providers offer immutable storage as an option. |

---

## 14. Control 12 - Network Infrastructure Management

*Purpose: Establish and maintain the secure management of network infrastructure.*

### 12.1 - Ensure Network Infrastructure is Up-to-Date

| Field | Detail |
|-------|--------|
| **What It Requires** | Ensure network infrastructure is kept up to date. Review for end-of-life products and update quarterly or more frequently. |
| **M365 Feature** | None - network infrastructure is outside M365 scope |
| **Admin Portal Path** | N/A |
| **M365 Coverage** | None |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Routers, switches, access points, and firewalls must be managed independently. MedCaribe uses consumer-grade ISP routers at 3 locations, which are typically not firmware-updated. Phase 4 of Project 1 roadmap addresses this with business-grade firewall deployment. |

### 12.6 - Use of DNS Filtering Services

| Field | Detail |
|-------|--------|
| **What It Requires** | Use DNS filtering services to block access to known malicious domains on all enterprise assets. |
| **M365 Feature** | Defender for Business (network protection on enrolled endpoints) |
| **Admin Portal Path** | Defender: security.microsoft.com > Settings > Endpoints > Advanced features > Network protection |
| **M365 Coverage** | Partial |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Defender network protection blocks malicious URLs on managed endpoints. For network-wide DNS filtering (all devices including IoT, printers, personal devices on guest Wi-Fi), a separate DNS filtering service is needed at the network level. |

---

## 15. Control 13 - Network Monitoring and Defense

*Purpose: Operate processes and tooling to establish and maintain comprehensive network monitoring and defense.*

### 13.1 - Centralize Security Event Alerting

| Field | Detail |
|-------|--------|
| **What It Requires** | Centralize security event alerting across enterprise assets. |
| **M365 Feature** | Microsoft 365 Defender portal (unified incident queue), Entra ID alerts, Defender for Business alerts |
| **Admin Portal Path** | Defender: security.microsoft.com > Incidents & alerts > Incidents |
| **M365 Coverage** | Full (for M365 ecosystem) |
| **MedCaribe Status** | Not Implemented |
| **Notes** | The Microsoft 365 Defender portal provides a unified view of incidents and alerts across email, identity, and endpoint. Configure alert notifications to email the IT Administrator and Operations Manager. |

---

## 16. Control 14 - Security Awareness and Skills Training

*Purpose: Establish and maintain a security awareness program to influence behavior among the workforce.*

### 14.1 - Establish and Maintain a Security Awareness Program

| Field | Detail |
|-------|--------|
| **What It Requires** | Establish and maintain a security awareness program. Review content annually. |
| **M365 Feature** | Microsoft Defender for Office 365 (Attack Simulation Training) |
| **Admin Portal Path** | Security: security.microsoft.com > Email & collaboration > Attack simulation training |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented - identified as Phase 3 action in Project 1 |
| **Notes** | M365 Business Premium includes Attack Simulation Training, which provides phishing simulations and training content. Can be supplemented with a third-party training platform for broader security awareness topics beyond phishing. |

### 14.2 - Train Workforce Members to Recognize Social Engineering Attacks

| Field | Detail |
|-------|--------|
| **What It Requires** | Train workforce to recognize social engineering attacks including phishing, pretexting, tailgating, and BEC. |
| **M365 Feature** | Defender for Office 365 (Attack Simulation Training - phishing simulations with built-in training modules) |
| **Admin Portal Path** | Security: security.microsoft.com > Email & collaboration > Attack simulation training > Simulations |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Create and launch phishing simulation campaigns targeting all staff. M365 provides realistic templates and tracks who clicked, reported, or completed training. Use results to identify staff who need additional coaching. |

### 14.3 - Train Workforce Members on Authentication Best Practices

| Field | Detail |
|-------|--------|
| **What It Requires** | Train on creating strong passwords, importance of not reusing passwords, and how to use MFA. |
| **M365 Feature** | Attack Simulation Training (training modules include authentication topics) |
| **Admin Portal Path** | Security: security.microsoft.com > Email & collaboration > Attack simulation training > Training campaigns |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Include authentication best practices in the security awareness program. Time this training with the MFA rollout so staff understand why MFA is being enforced. |

### 14.4 - Train Workforce on Data Handling Best Practices

| Field | Detail |
|-------|--------|
| **What It Requires** | Train on proper data storage, transfer, archiving, and destruction. |
| **M365 Feature** | Attack Simulation Training (data handling modules available) |
| **Admin Portal Path** | Security: security.microsoft.com > Email & collaboration > Attack simulation training > Training campaigns |
| **M365 Coverage** | Partial |
| **MedCaribe Status** | Not Implemented |
| **Notes** | M365 provides some built-in training content on data handling. For MedCaribe-specific requirements (Data Classification Policy, WhatsApp prohibition, USB restrictions), custom training content aligned to POL-001 and POL-004 will be needed. |

### 14.5 - Train Workforce on Causes of Unintentional Data Exposure

| Field | Detail |
|-------|--------|
| **What It Requires** | Train on causes of unintentional data exposure including misconfigured sharing, accidental email to wrong recipient, and loss of portable devices. |
| **M365 Feature** | Attack Simulation Training, M365 MailTips (external recipient warnings) |
| **Admin Portal Path** | Security: security.microsoft.com > Email & collaboration > Attack simulation training. Exchange: admin.exchange.microsoft.com > Mail flow > Rules (external recipient warning) |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Configure Exchange MailTips to warn users when sending to external recipients. Combine with training on common data exposure scenarios relevant to MedCaribe (e.g., forwarding patient data to personal email, sharing OneDrive links publicly). |

### 14.8 - Train Workforce on Incident Reporting

| Field | Detail |
|-------|--------|
| **What It Requires** | Train workforce on how to identify and report security incidents. |
| **M365 Feature** | Attack Simulation Training (incident reporting modules), Defender for Office 365 (Report Message add-in) |
| **Admin Portal Path** | Security: security.microsoft.com > Email & collaboration > Attack simulation training. Outlook: deploy Report Message add-in via admin.microsoft.com > Settings > Integrated apps |
| **M365 Coverage** | Full |
| **MedCaribe Status** | Not Implemented |
| **Notes** | Deploy the "Report Message" or "Report Phishing" add-in to all Outlook clients. This gives staff a one-click button to report suspicious emails directly to the security team. Combine with training on the IR Policy (POL-003) reporting procedures. |

---

## 17. Control 15 - Service Provider Management

*Purpose: Develop a process to evaluate service providers who hold sensitive data or are responsible for critical IT platforms.*

### 15.1 - Establish and Maintain an Inventory of Service Providers

| Field | Detail |
|-------|--------|
| **What It Requires** | Inventory all service providers including classification, contact information, and data they handle. Review annually. |
| **M365 Feature** | Entra ID (Enterprise Applications - shows all connected third-party apps and services) |
| **Admin Portal Path** | Entra ID: entra.microsoft.com > Applications > Enterprise applications |
| **M365 Coverage** | Partial |
| **MedCaribe Status** | Not Implemented - Vendor Risk Policy (POL-005) defines the process |
| **Notes** | Entra ID shows OAuth-connected apps but does not inventory all vendors (e.g., EHR vendor, insurance portals, external labs). The vendor inventory from POL-005 must be maintained as a separate governance document. |

### 15.4 - Ensure Service Provider Contracts Include Security Requirements

| Field | Detail |
|-------|--------|
| **What It Requires** | Ensure contracts include security requirements, data handling, incident notification, and audit rights. |
| **M365 Feature** | None - this is a contractual/governance control |
| **Admin Portal Path** | N/A |
| **M365 Coverage** | None |
| **MedCaribe Status** | Not Implemented - contractual requirements defined in POL-005 |
| **Notes** | M365 cannot enforce vendor contracts. However, Microsoft's own DPA (Data Processing Agreement) for M365 satisfies many of these requirements for the Microsoft relationship specifically. Other vendors (EHR, QuickBooks, labs) require separate contract review per POL-005. |

---

## 18. Control 16 - Application Software Security

*Purpose: Manage the security lifecycle of in-house developed, hosted, or acquired software.*

### 16.1 - Establish and Maintain a Secure Application Development Process

| Field | Detail |
|-------|--------|
| **What It Requires** | Establish a secure development process for in-house developed software. |
| **M365 Feature** | N/A - MedCaribe does not develop software in-house |
| **Admin Portal Path** | N/A |
| **M365 Coverage** | Not Applicable |
| **MedCaribe Status** | Not Applicable |
| **Notes** | MedCaribe uses commercial off-the-shelf (COTS) and SaaS applications exclusively. This safeguard is not applicable to the current environment. If custom development is introduced in the future, this safeguard should be reassessed. |

### 16.11 - Use Standard Hardening Configuration Templates for Databases

| Field | Detail |
|-------|--------|
| **What It Requires** | Use standard hardening templates for database servers. |
| **M365 Feature** | N/A - MedCaribe does not operate database servers; all databases are SaaS-hosted |
| **Admin Portal Path** | N/A |
| **M365 Coverage** | Not Applicable |
| **MedCaribe Status** | Not Applicable |
| **Notes** | All MedCaribe databases are managed by SaaS vendors (CloudMed EHR, QuickBooks, M365). Vendor responsibility for database hardening is covered under vendor risk management (Control 15). |

---

## 19. Control 17 - Incident Response Management

*Purpose: Establish a program to develop and maintain an incident response capability.*

### 17.1 - Designate Personnel to Manage Incident Handling

| Field | Detail |
|-------|--------|
| **What It Requires** | Designate one key person and at least one backup to manage the incident handling process. |
| **M365 Feature** | None - this is a governance/personnel control |
| **Admin Portal Path** | N/A |
| **M365 Coverage** | None |
| **MedCaribe Status** | Implemented via Project 1 - Incident Coordinator (Operations Manager) and alternates defined in IR Plan |
| **Notes** | The IR Plan from Project 1 designates K. Rampersad as Incident Coordinator with S. Mohammed as alternate. Contact details and escalation paths documented. |

### 17.2 - Establish and Maintain Contact Information for Reporting Security Incidents

| Field | Detail |
|-------|--------|
| **What It Requires** | Establish and maintain contact information for parties who need to be informed of security incidents. Review annually. |
| **M365 Feature** | None - governance document |
| **Admin Portal Path** | N/A |
| **M365 Coverage** | None |
| **MedCaribe Status** | Implemented via Project 1 - contact list in IR Plan and Escalation Decision Tree |
| **Notes** | Internal and external contacts (including Information Commissioner, TTPS Cyber Crime Unit, insurance, legal counsel) documented in the Escalation Decision Tree. |

### 17.3 - Establish and Maintain an Enterprise Process for Reporting Incidents

| Field | Detail |
|-------|--------|
| **What It Requires** | Establish a process for workforce to report security incidents. Must include timeline and escalation criteria. |
| **M365 Feature** | Defender for Office 365 (Report Message add-in for email-based reporting) |
| **Admin Portal Path** | Outlook add-in deployment via admin.microsoft.com > Settings > Integrated apps |
| **M365 Coverage** | Partial |
| **MedCaribe Status** | Implemented via Project 1 (policy and process); technical reporting tools not yet deployed |
| **Notes** | The IR Policy (POL-003) defines the reporting process. The Report Message add-in provides a technical mechanism for reporting suspicious emails. General incident reporting (non-email) follows the verbal/email process defined in the policy. |

### 17.4 - Establish and Maintain an Incident Response Process

| Field | Detail |
|-------|--------|
| **What It Requires** | Establish and maintain an incident response process addressing roles, communication, escalation, and management phases. Review annually. |
| **M365 Feature** | None - governance document |
| **Admin Portal Path** | N/A |
| **M365 Coverage** | None |
| **MedCaribe Status** | Implemented via Project 1 - Full IR Plan with NIST SP 800-61 lifecycle, containment procedures, and decision tree |
| **Notes** | This safeguard is fully satisfied by the Incident Response Plan and Escalation Decision Tree from Project 1. Annual review and post-incident updates required. |

### 17.5 - Assign Key Roles and Responsibilities

| Field | Detail |
|-------|--------|
| **What It Requires** | Assign key roles and responsibilities for incident response including staff from legal, IT, and communications. |
| **M365 Feature** | None - governance document |
| **Admin Portal Path** | N/A |
| **M365 Coverage** | None |
| **MedCaribe Status** | Implemented via Project 1 - IR Team defined with Incident Coordinator, Technical Lead, Decision Authority, and Communications Lead |
| **Notes** | Roles assigned in the IR Plan. External contacts (legal counsel, external IR support) identified as TBD items requiring establishment. |

### 17.6 - Define Mechanisms for Communicating During Incident Response

| Field | Detail |
|-------|--------|
| **What It Requires** | Define communication mechanisms for incident response including out-of-band (non-email) channels. |
| **M365 Feature** | Microsoft Teams (if email is compromised, Teams may still be available), phone contacts in IR Plan |
| **Admin Portal Path** | N/A |
| **M365 Coverage** | Partial |
| **MedCaribe Status** | Partial - phone numbers documented in IR Plan; no formal out-of-band channel established |
| **Notes** | If M365 is fully compromised, Teams and email are unavailable. The IR Plan includes direct phone numbers as the out-of-band fallback. Consider establishing a non-M365 group chat (e.g., Signal group for the IR team) as an additional backup communication channel. |

### 17.7 - Conduct Routine Incident Response Exercises

| Field | Detail |
|-------|--------|
| **What It Requires** | Conduct routine exercises (tabletop or simulated) to test the IR process. |
| **M365 Feature** | Defender for Office 365 (Attack Simulation Training can serve as a technical exercise component) |
| **Admin Portal Path** | Security: security.microsoft.com > Email & collaboration > Attack simulation training |
| **M365 Coverage** | Partial |
| **MedCaribe Status** | Not Implemented - first tabletop exercise planned for Phase 3 (Month 4-6) in Project 1 roadmap |
| **Notes** | Phishing simulations via M365 test one aspect of IR readiness. Full tabletop exercises (BEC scenario, ransomware scenario) as defined in the Project 1 roadmap require manual facilitation. M365 attack simulations can supplement but not replace tabletop exercises. |

### 17.9 - Establish and Maintain Security Incident Thresholds

| Field | Detail |
|-------|--------|
| **What It Requires** | Establish thresholds for security incident severity classification, including at minimum differentiating between an incident and an event. |
| **M365 Feature** | None - governance document |
| **Admin Portal Path** | N/A |
| **M365 Coverage** | None |
| **MedCaribe Status** | Implemented via Project 1 - IR Policy defines four severity levels (Critical, High, Medium, Low) with clear criteria and examples |
| **Notes** | Severity thresholds and classification criteria documented in the IR Policy (POL-003) and the Escalation Decision Tree. |

---

## 20. Coverage Summary

| CIS Control Family | IG1 Safeguards | M365 Full Coverage | M365 Partial | M365 None | Not Applicable |
|--------------------|-----------|--------------------|-------------|-----------|----------------|
| 1. Enterprise Asset Inventory | 2 | 0 | 2 | 0 | 0 |
| 2. Software Asset Inventory | 3 | 1 | 1 | 0 | 1 |
| 3. Data Protection | 10 | 7 | 3 | 0 | 0 |
| 4. Secure Configuration | 3 | 2 | 1 | 0 | 0 |
| 5. Account Management | 4 | 3 | 1 | 0 | 0 |
| 6. Access Management | 5 | 5 | 0 | 0 | 0 |
| 7. Vulnerability Management | 4 | 3 | 1 | 0 | 0 |
| 8. Audit Log Management | 4 | 4 | 0 | 0 | 0 |
| 9. Email and Web Protections | 4 | 3 | 1 | 0 | 0 |
| 10. Malware Defenses | 4 | 4 | 0 | 0 | 0 |
| 11. Data Recovery | 4 | 0 | 1 | 3 | 0 |
| 12. Network Infrastructure | 2 | 0 | 1 | 1 | 0 |
| 13. Network Monitoring | 1 | 1 | 0 | 0 | 0 |
| 14. Security Awareness | 6 | 5 | 1 | 0 | 0 |
| 15. Service Provider Mgmt | 2 | 0 | 1 | 1 | 0 |
| 16. Application Security | 2 | 0 | 0 | 0 | 2 |
| 17. Incident Response | 7 | 0 | 3 | 4 | 0 |
| **TOTAL** | **56** | **34** | **12** | **8** | **2** |

**Summary: 34 safeguards (61%) fully covered by M365, 12 (21%) partially covered, 8 (14%) not covered, 2 (4%) not applicable.**

---

## 21. Document Control

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | March 2026 | J. Maitland | Initial mapping - all 56 IG1 safeguards |

**Next Review:** March 2027 or upon significant M365 feature changes, licensing changes, or CIS Controls updates.
