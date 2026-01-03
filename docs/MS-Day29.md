# 🛡️ Mini-Project-Final – Reynaldo Martinez

**Microsoft Defender Investigation Report**  
*SOC / DFIR / Blue Team Portfolio Project*

---

## 📌 Overview

This mini-project demonstrates a **simulated end-to-end security investigation** using **Microsoft Defender** across **email, identity, and endpoint** security layers.  
The objective was to validate detection, prevention, and correlation capabilities in a realistic attack scenario.

> ⚠️ All activities were performed in a **controlled lab environment** for educational and portfolio purposes.

---

## 🧪 Simulated Attack Scenarios

- **Phishing Email Simulation**
- **Risky Cloud Sign-In from Foreign Geography**
- **Endpoint Persistence via Atomic Red Team**

---

## 🔍 Findings (What did you find)

- A phishing email using an **invoice lure** was successfully delivered and marked as **Allowed**.
- A suspicious sign-in attempt from **Netherlands (VPN-based)** was **blocked** by Conditional Access.
- A **registry-based persistence technique** using obfuscated PowerShell was **detected** by Defender for Endpoint.
- Events across email, identity, and endpoint were correlated into a single incident narrative.

---

## 🧠 Investigation Summary (What happened)

The investigation simulated a common attacker lifecycle:
1. Initial access via phishing
2. Suspicious authentication attempt
3. Endpoint persistence activity

While the phishing email bypassed preventive controls, identity and endpoint protections successfully detected and/or blocked malicious behavior. This highlights the importance of **defense-in-depth** and cross-domain telemetry correlation.

---

## 🧾 Incident Analysis (Who, What, When, Where, Why, How)

### 👤 Who
- **User Account:** `jenny@30mydfir.onmicrosoft.com`
- **Threat Actor:** Simulated attacker activity

---

### ❓ What
- Phishing email delivery
- Risky sign-in attempt from foreign country
- Endpoint persistence attempt using PowerShell and registry run keys

---

### ⏰ When (UTC-5)
- **Phishing Email:** Dec 26, 2025 – 12:49 PM  
- **Risky Sign-In:** Dec 26, 2025 (Blocked)  
- **Endpoint Detection:** Dec 29, 2025 – 1:38:40 PM  

---

### 🌍 Where
- **Email:** Exchange Online
- **Identity:** Microsoft Entra ID
- **Endpoint:** Windows 11 VM
- **Sign-in Location:** Naaldwijk, Zuid-Holland, Netherlands  
- **IP Address:** `93.190.140.117`

---

### ❓ Why
- Activity was intentionally simulated to test Microsoft Defender detection and response capabilities.
- In a real scenario, this behavior aligns with attacker persistence following initial access.

---

### ⚙️ How
- **Initial Access:** Invoice-themed phishing email
- **Identity Abuse:** VPN-based sign-in from unusual geography
- **Persistence:** Atomic Red Team technique `T1547.001` using obfuscated PowerShell

---

## ❓ Investigation Questions – Answered

### What triggered the incident?
A simulated phishing email followed by suspicious identity and endpoint activity.

### What was the initial access vector?
Email-based phishing.

### What user accounts were impacted?
- `jenny@30mydfir.onmicrosoft.com`

### Was there suspicious sign-in activity?
Yes. A foreign sign-in was blocked by Conditional Access (Error Code `53003`).

### What actions occurred on the endpoint?
- Obfuscated PowerShell execution  
- Registry-based persistence attempt  
- Script artifact creation  

### What timeline can be built?
1. Phishing email delivered
2. Risky sign-in blocked
3. Endpoint persistence detected

### How were signals correlated?
- Same user account
- Related timestamps
- MITRE ATT&CK technique mapping
- Defender telemetry across multiple domains

### Any surprising behavior?
- Phishing email was allowed despite containing a known phishing test URL.
- Endpoint activity was detected but not automatically blocked.

### If this were a real incident, how would you respond?
- Treat as confirmed incident
- Assume credential exposure
- Escalate for containment and remediation

---

## 🛠️ Recommendations

### ✉️ Email Security
- Harden anti-phishing policies
- Enable Safe Links & Safe Attachments in blocking mode
- Improve user awareness training

### 🔐 Identity Protection
- Enforce MFA for all users
- Strengthen Conditional Access policies
- Use risk-based and location-based access controls

### 💻 Endpoint Protection
- Enable automatic remediation
- Restrict PowerShell execution
- Monitor registry persistence mechanisms

### 🚨 Incident Response
- Reset affected credentials
- Isolate impacted endpoint
- Perform forensic review
- Document and close detection gaps

---

## 🎯 MITRE ATT&CK Mapping

| Tactic | Technique |
|------|---------|
| Initial Access | T1566 – Phishing |
| Persistence | T1547.001 – Registry Run Keys |
| Execution | T1059.001 – PowerShell |

---

## 🏁 Conclusion

This project demonstrates how **Microsoft Defender’s layered security approach** enables effective detection and correlation across email, identity, and endpoint telemetry. While no single control prevented all activity, combined signals provided strong visibility and actionable insights—mirroring real SOC investigation workflows.

---

---

## 📎 Appendix A – KQL Queries (Investigation Reference)

> The following KQL queries represent **example investigative queries** that could be used to validate and correlate findings in Microsoft Defender and Microsoft Sentinel.  

---

## ✉️ Email Investigation Queries

### Identify the Phishing Email
```kql
EmailEvents
| where RecipientEmailAddress == "jenny@30mydfir.onmicrosoft.com"
| where Subject contains "Invoice"
| project Timestamp, SenderFromAddress, Subject, DeliveryAction, NetworkMessageId
| order by Timestamp desc

Extract URLs from Email Content
EmailUrlInfo
| where Url contains "testsafebrowsing.appspot.com"
| project Timestamp, Url, NetworkMessageId

Check for User Interaction (URL Clicks)
UrlClickEvents
| where AccountUpn == "jenny@30mydfir.onmicrosoft.com"
| project Timestamp, Url, ActionType
| order by Timestamp desc

🔐 Identity & Sign-In Investigation Queries
Review Blocked Sign-In Attempts
SignInLogs
| where UserPrincipalName == "jenny@30mydfir.onmicrosoft.com"
| where ResultType == 53003
| project TimeGenerated, IPAddress, Location, ResultDescription, ConditionalAccessStatus
| order by TimeGenerated desc

Detect Sign-Ins from Unusual Locations
SignInLogs
| where UserPrincipalName == "jenny@30mydfir.onmicrosoft.com"
| summarize count() by Location, IPAddress

💻 Endpoint Investigation Queries (Microsoft Defender for Endpoint)
PowerShell Process Execution
DeviceProcessEvents
| where FileName == "powershell.exe"
| project Timestamp, DeviceName, ProcessCommandLine, InitiatingProcessFileName
| order by Timestamp desc

Detect Obfuscated or Suspicious PowerShell Activity
DeviceProcessEvents
| where FileName == "powershell.exe"
| where ProcessCommandLine has_any ("-enc", "IEX", "Invoke-", "DownloadString")
| project Timestamp, DeviceName, ProcessCommandLine

Registry Persistence (Run Keys)
DeviceRegistryEvents
| where RegistryKey has_any ("Run", "RunOnce")
| project Timestamp, DeviceName, RegistryKey, RegistryValueName, RegistryValueData
| order by Timestamp desc

Suspicious Script or Artifact Creation
DeviceFileEvents
| where FileName contains "_PSScriptPolicyTest"
| project Timestamp, DeviceName, FileName, FolderPath, ActionType

🌐 Network Activity Queries
Outbound Network Connections from PowerShell
DeviceNetworkEvents
| where InitiatingProcessFileName == "powershell.exe"
| project Timestamp, DeviceName, RemoteIP, RemoteUrl, RemotePort
| order by Timestamp desc

🧠 Correlation & Hunting Queries
Correlate User Activity Across Email, Identity, and Endpoint
union EmailEvents, SignInLogs, DeviceProcessEvents
| where tostring(UserPrincipalName) == "jenny@30mydfir.onmicrosoft.com"
| project TimeGenerated, ActionType, DeviceName, IPAddress
| order by TimeGenerated asc

Identify Potential Persistence Techniques
DeviceEvents
| where ActionType contains "Registry"
| where AdditionalFields has "Run"
| project Timestamp, DeviceName, ActionType, AdditionalFields



## 📂 Repository Purpose

This repository is part of my **cybersecurity portfolio**, showcasing:
- SOC investigation skills
- Microsoft Defender expertise
- MITRE ATT&CK mapping
- Incident analysis & reporting

👤 **Author:** Reynaldo Martinez  
🔐 **Focus:** SOC Analyst | DFIR | Microsoft Security

