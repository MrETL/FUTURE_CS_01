# OWASP Juice Shop Vulnerability Assessment Report

**Cyber Security Assessment**  
**Author:** Dilnessa Aemro  
**Date:** March 2025

---

## Project Overview

This repository contains a comprehensive vulnerability assessment report for the OWASP Juice Shop demo application. The assessment was conducted as part of the , focusing on identifying common security weaknesses in a live website using read-only and passive scanning techniques.

---

## Target Information

| Field | Details |
|-------|---------|
| **Target** | OWASP Juice Shop |
| **URL** | https://demo.owasp-juice.shop/ |
| **Scope** | Public-facing endpoints, passive scanning, configuration analysis |
| **Assessment Type** | Vulnerability Assessment (Read-Only) |

---

## Tools Used

| Tool | Version | Purpose |
|------|---------|---------|
| OWASP ZAP | 2.17.0 | Automated vulnerability scanning |
| Burp Suite | Community/Professional | Manual testing, request interception |
| Nmap | 7.98 | Port scanning and service detection |
| Browser DevTools | Chrome/Firefox | Header inspection |

---

## Scope & Ethics

### Allowed
- Public-facing pages only
- Passive scanning
- Header checks
- Configuration analysis

### Not Allowed
- Login bypass exploitation (documented only)
- Brute force attacks
- Denial-of-Service (DoS)
- Any activity that can harm the website

---

## Repository Structure

```
FUTURE_CS_01/
├── evidence/
│   ├── screenshots/          # Screenshot evidence of findings
│   │   ├── sqli_login_bypass.png
│   │   ├── sqli_admin_takeover_from_users_account.png
│   │   ├── weak_password_email.png
│   │   ├── weak_security_answer.png
│   │   ├── zap_csp_failure.png
│   │   ├── zap_cors.png
│   │   └── ... (other findings)
│   └── tool_outputs/         # Raw tool outputs
│       ├── nmap_basic.txt
│       ├── nmap_detailed.txt
│       └── zap-report.html
├── report/
│   ├── VULNERABILITY_ASSESSMENT_REPORT.pdf
│   └── VULNERABILITY_ASSESSMENT_REPORT_COMPILED.md
├── evidence/
│   ├── MANUAL_TESTING_CHECKLIST.md
│   └── ZAP_FINDINGS_FOR_REPORT.md
└── README.md
```

---

## Key Findings Summary

| Risk Level | Count | Findings |
|------------|-------|----------|
| **Critical** | 2 | SQL Injection - Login Bypass, SQL Injection - Admin Takeover |
| **Medium** | 3 | Weak Password Policy, CSP Issues, CORS Misconfiguration |
| **Low** | 2 | Server Version Leak, Timestamp Disclosure |
| **Informational** | 3 | Tech Detection (Apache, UNIX), Modern Web App |

---

## Vulnerabilities Identified

### Critical Risk
1. **SQL Injection - Login Bypass** - Authentication can be bypassed using `' OR 1=1--` payload
2. **SQL Injection - Admin Account Takeover** - SQLi grants admin access instead of user account

### Medium Risk
3. **Weak Password Policy** - System allows email as password and security answer
4. **CSP Header Issues** - Missing/fallback CSP directives
5. **CORS Misconfiguration** - Wildcard (*) origin allows any domain access

### Low Risk
6. **Server Version Leak** - Apache 2.4.66 version disclosed in headers
7. **Timestamp Disclosure** - Unix timestamps reveal system information

---

## Report Files

- **Full Report (PDF):** `report/VULNERABILITY_ASSESSMENT_REPORT.pdf`
- **Compiled Report (Markdown):** `report/VULNERABILITY_ASSESSMENT_REPORT_COMPILED.md`

---

## How to View the Report

1. **PDF Version:** Open `report/VULNERABILITY_ASSESSMENT_REPORT.pdf` in any PDF reader
2. **Markdown Version:** View `report/VULNERABILITY_ASSESSMENT_REPORT_COMPILED.md` on GitHub or in any Markdown viewer

---

## Methodology

1. **Reconnaissance:** Nmap scanning to identify exposed services
2. **Automated Scanning:** OWASP ZAP passive scan for common vulnerabilities
3. **Manual Testing:** Burp Suite for authentication bypass, SQL injection, business logic flaws
4. **Documentation:** Screenshot evidence and detailed findings recording

---

## Disclaimer

This vulnerability assessment was conducted on the **OWASP Juice Shop demo application** (https://demo.owasp-juice.shop/), which is an intentionally vulnerable web application designed for security training and testing purposes. All testing was performed within ethical boundaries and read-only scope as specified in the guidelines.

**Do not test these techniques on production systems without proper authorization.**

---

## References

- [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/)
- [OWASP ZAP](https://www.zaproxy.org/)


---

**Report Prepared By:** Dilnessa Aemro  
**Program:**   
**Date:** March 2025
