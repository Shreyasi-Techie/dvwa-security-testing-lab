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

## Methodology

Reconnaissance

↓

Input Analysis

↓

Payload Testing

↓

Validation

↓

Evidence Collection

↓

Documentation

↓

Remediation

---

## Documentation

- 📄 [Findings](findings.md)
- 🛡️ [Remediation](remediation.md)
- 📑 [Assessment Report](report/report.md)
- 🖼️ [Evidence & Screenshots](screenshots.md)

---

# SQL Injection

## Objective

Demonstrate SQL Injection testing using DVWA and Burp Suite.

## Environment

- DVWA
- Kali Linux
- Burp Suite Community Edition
- Apache
- PHP
- MySQL

## Vulnerability

The application directly inserts user-controlled input into an SQL query without parameterized statements.

Payload used:

```sql
1' OR '1'='1
```

Result:

The application returned multiple database records instead of one, confirming successful SQL Injection.

## Evidence

| Screenshot | Description |
|------------|-------------|
| 01 | DVWA Security Level |
| 02 | Normal Application Behaviour |
| 03 | Burp Proxy Capture |
| 04 | SQL Injection using Burp Repeater |
| 05 | Vulnerable Source Code |

## Skills Demonstrated

- Burp Suite
- HTTP Request Analysis
- SQL Injection Testing
- Command Injection Testing
- XSS Validation
- Security Documentation

---

## Disclaimer

Testing was performed only in an authorized educational laboratory.
