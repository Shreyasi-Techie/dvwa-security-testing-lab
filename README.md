# 🔐 DVWA Security Testing Laboratory

![Platform](https://img.shields.io/badge/Platform-Kali%20Linux-blue)
![Target](https://img.shields.io/badge/Application-DVWA-red)
![Tools](https://img.shields.io/badge/Tools-Burp%20Suite%20%7C%20Browser-green)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

## Overview

This repository documents security testing performed against **Damn Vulnerable Web Application (DVWA)** in an authorized laboratory environment.

The purpose of the assessment was to understand common web application vulnerabilities and their mitigation.

---

## Vulnerabilities Assessed

- SQL Injection
- Cross-Site Scripting (Reflected)
- Command Injection

---

## Lab Environment

| Component | Details |
|----------|---------|
| Attacker | Kali Linux |
| Target | DVWA |
| Environment | VirtualBox |
| Testing Type | Authorized Lab |

---

# Methodology

The assessment followed a structured testing methodology:

1. Reconnaissance
2. Intercepting HTTP traffic using Burp Suite
3. Manual payload injection
4. Request modification
5. Response analysis
6. Vulnerability validation
7. Risk assessment
8. Documentation
9. Remediation recommendations

---

# Key Findings

## 1. SQL Injection

**Severity:** High

The application concatenates user-controlled input directly into SQL queries without validation or parameterized statements.

**Impact**

- Authentication bypass
- Database enumeration
- Sensitive information disclosure
- Potential database compromise

Documentation:

```
sql-injection/
```

## 2. Reflected Cross-Site Scripting (XSS)

**Severity:** High

The application reflects unsanitized user input directly into the HTML response, allowing arbitrary JavaScript execution in the user's browser.

### Demonstrated Payloads

```html
<script>alert(1)</script>
```

```html
<script>alert(document.cookie)</script>
```

### Impact

- JavaScript execution
- Session cookie disclosure
- Session hijacking
- Phishing attacks
- Client-side manipulation

Documentation:

```
reflected-xss/
```

# Skills Demonstrated

- Web Application Security Testing
- Vulnerability Validation
- HTTP Request Analysis
- Burp Suite Proxy & Repeater
- Manual Security Testing
- OWASP Top 10
- Secure Coding Awareness
- Technical Documentation
- Vulnerability Reporting

---

# Learning Outcomes

Through this assessment I gained practical experience in:

- Identifying web application vulnerabilities
- Understanding HTTP request/response flows
- Exploiting vulnerabilities safely within a controlled lab
- Assessing business and technical impact
- Preparing professional security assessment reports
- Recommending secure coding practices

---

## Disclaimer

Testing was performed only in an authorized educational laboratory.
