# 🔴 Red Team Penetration Testing Portfolio  
### by **Samuel Djuarsa**  
GitHub: https://github.com/caixuekang777-sys

This repository showcases my hands-on experience performing a full penetration test on an intentionally vulnerable web application (`dibishop.duckdns.org`).  
All testing was performed ethically, safely, and with explicit authorization in a controlled lab environment.

The portfolio demonstrates end-to-end Red Team methodology:
- Reconnaissance  
- Scanning & Vulnerability Discovery  
- Exploitation  
- Post-Exploitation & Privilege Escalation (conceptual)  
- Reporting, Analysis & Mitigations  

Sanitized evidence and technical appendices are included to meet ethical and legal requirements.

---

# 🧭 1. Portfolio Introduction

This project simulates a real-world engagement against a modern e-commerce web application.  
The goal was to identify vulnerabilities, demonstrate controlled exploitation in a safe environment, and deliver actionable remediation guidance.

**Testing Methodology**
- Hybrid approach: **Black-Box + Grey-Box**
- Based on **OWASP Web Security Testing Guide (WSTG)**
- Vulnerability scoring: **CVSS v3.1**
- Ethical limitations:
  - No DoS attacks  
  - No brute-force account lockouts  
  - No testing outside approved domain  
  - No destructive actions  

**Objectives**
- Develop and demonstrate practical penetration testing skills.  
- Identify and validate real vulnerabilities.  
- Produce a comprehensive security report following professional standards.  
- Recommend practical mitigations for developers and system owners.

---

# 🌐 2. Reconnaissance & Scanning

This phase focused on mapping the application’s attack surface.

## 🔍 2.1 Information Gathering
Tools used:
- `Nslookup`
- `Whois`
- `Nmap`
- `Nikto`
- `OWASP ZAP`

**Key observations:**
- Public-facing web application at `dibishop.duckdns.org`
- Apache-based environment  
- Exposed endpoints, including:
  - `/customer_register.php`
  - `/admin_area/` (restricted)
- Lack of modern HTTP security headers

## 📡 2.2 Scanning Summary
| Tool | Purpose | Sanitized Findings |
|------|---------|--------------------|
| **Nmap** | Service enumeration, HTTP detection | Open ports matched typical web stack |
| **Nikto** | Vulnerability scan | Missing CSP header, outdated components |
| **ZAP** | Active scanning | Reflected XSS indicators |

The scanning results guided the exploitation phase.

---

# 💥 3. Exploitation Documentation  
*(Evidence sanitized — no sensitive data exposed)*  
All exploitation below was performed in an **authorized controlled lab** and validated against the approved scope.

## ⚠️ 3.1 Vulnerability 1 — Reflected Cross-Site Scripting (XSS)  
**Severity:** Medium (CVSS 6.8)  
**Affected endpoint:** `customer_register.php`

### ✔️ Description  
User input was reflected unsafely in the response without output encoding, enabling JavaScript execution.

### ✔️ Sanitized Proof of Concept
This payload executed successfully, confirming reflected XSS.

### ✔️ Impact  
- Possible session theft  
- Defacement  
- Unauthorized actions via victim's browser  

### ✔️ Recommended Fix  
- Apply strict input validation  
- Use htmlspecialchars()  
- Implement proper output encoding  
- Introduce server-side filtering

---

## ⚠️ 3.2 Vulnerability 2 — Content Security Policy (CSP) Header Missing  
**Severity:** Medium (CVSS 5.3)  
**Affected scope:** All endpoints (`/*`)

### ✔️ Description  
The application lacked a **Content Security Policy**, significantly increasing XSS risk.

### ✔️ Sanitized Evidence  
- SecurityHeaders.com score: **F**  
- `curl -I` response showed no `Content-Security-Policy` header  

### ✔️ Impact  
- Browser accepts scripts from any source  
- Malware injection possible  
- Higher impact when combined with existing XSS

### ✔️ Recommended Fix  
- Implement `Content-Security-Policy: default-src 'self'`  
- Add headers:
  - `X-Content-Type-Options: nosniff`
  - `X-Frame-Options: DENY`
- Review external scripts loading

---

# 🛠️ 4. Post-Exploitation & Privilege Escalation (Conceptual)

Because this was a **controlled, ethical engagement**, no real system compromise was performed beyond safe verification.

However, based on the vulnerabilities found, realistic attacker actions could include:

### 🔑 4.1 Session Hijacking (via XSS)
- Stealing session cookies  
- Acting as the logged-in user  
- Pivoting into account manipulation  

### 🔒 4.2 Account Takeover (conceptual)
XSS could enable:
- Password change attempts  
- CSRF-like forced actions  
- Social engineering payloads

### 🚀 4.3 Privilege Escalation Paths (theoretical)
An attacker could attempt:
- Accessing `/admin_area/` after session theft  
- Altering business logic via injected scripts  
- Modifying requests through captured session tokens  

All post-exploitation considerations were kept theoretical — **no harmful action was executed**.

---

# 📑 5. Final Report & Portfolio Finalization

This repository includes:
- 📘 **Technical Appendix** (recon output, nmap results, XSS logs) — sanitized  
- 📄 **Full Penetration Testing Report (PDF)** — with findings, CVSS scoring, recommendations  
- 📂 **Evidence Folder** — screenshots & redacted captures  
- 🛠️ **Tooling List**  
  - OWASP ZAP  
  - Nmap  
  - Nikto  
  - Nslookup  
  - Whois  

### 🎯 What This Portfolio Demonstrates
- Strong analytical skills  
- Clear technical writing  
- Ethical red team methodology  
- Knowledge of OWASP & CVSS  
- Ability to recommend practical mitigations  
- Professional reporting discipline  

---

# 🔚 Conclusion

This portfolio demonstrates my practical capabilities in:
- Web penetration testing  
- Vulnerability discovery and validation  
- Technical analysis  
- Ethical red team operations  
- Professional cybersecurity documentation  

I am committed to continuing my development in cybersecurity and building more advanced projects in Red Team, Blue Team, and security engineering.

---

# 📬 Contact
**Samuel Djuarsa**  
- GitHub: https://github.com/caixuekang777-sys  
- LinkedIn: https://www.linkedin.com/in/samuel-djuarsa-034787300/   
