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

## 📂 Repository Purpose

This repository is part of my **cybersecurity portfolio**, showcasing:
- SOC investigation skills
- Microsoft Defender expertise
- MITRE ATT&CK mapping
- Incident analysis & reporting

👤 **Author:** Reynaldo Martinez  
🔐 **Focus:** SOC Analyst | DFIR | Microsoft Security

