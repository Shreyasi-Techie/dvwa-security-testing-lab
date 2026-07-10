# Reflected Cross-Site Scripting (XSS) Assessment

## Overview

This directory documents the assessment of the **Reflected Cross-Site Scripting (XSS)** vulnerability in the **Damn Vulnerable Web Application (DVWA)** performed within an isolated laboratory environment.

The objective of this assessment was to determine whether user-controlled input was reflected in the application's response without proper validation or output encoding, allowing arbitrary JavaScript execution in a user's browser.

Testing was conducted using **Burp Suite**, browser developer tools, and manual payload injection techniques.

---

## Objective

- Identify reflected XSS vulnerabilities.
- Capture and analyze HTTP requests and responses using Burp Suite.
- Validate arbitrary JavaScript execution.
- Assess the potential impact of the vulnerability.
- Document findings and recommend secure coding practices.

---

## Lab Environment

| Component | Details |
|-----------|---------|
| Target Application | Damn Vulnerable Web Application (DVWA) |
| Operating System | Kali Linux |
| Web Server | Apache |
| Database | MySQL |
| Proxy Tool | Burp Suite Community Edition |
| Browser | Firefox |
| Security Level | Low |

---

## Testing Methodology

1. Configure DVWA security level to **Low**.
2. Navigate to the **Reflected XSS** module.
3. Capture the HTTP request using Burp Suite Proxy.
4. Send the request to Burp Repeater.
5. Modify the `name` parameter with JavaScript payloads.
6. Analyze the HTTP response.
7. Verify JavaScript execution in the browser.
8. Document findings and remediation recommendations.

---

## Payloads Tested

### Basic JavaScript Execution

```html
<script>alert(1)</script>
```

### Cookie Disclosure Demonstration

```html
<script>alert(document.cookie)</script>
```

> These payloads were executed only within the intentionally vulnerable DVWA laboratory environment for educational purposes.

---

## Key Findings

- Successfully identified a Reflected Cross-Site Scripting vulnerability.
- Verified that user input was reflected without sanitization.
- Confirmed arbitrary JavaScript execution in the browser.
- Demonstrated access to client-side cookies that were not protected with the `HttpOnly` flag.
- Verified improper output encoding and insufficient input validation.

---

## Skills Demonstrated

- Burp Suite Proxy
- Burp Suite Repeater
- HTTP Request & Response Analysis
- Manual Web Application Security Testing
- Cross-Site Scripting (XSS) Validation
- Browser Developer Tools
- OWASP Top 10 Awareness
- Technical Documentation
- Vulnerability Reporting

---

## Repository Contents

```
reflected-xss/

├── README.md
├── findings.md
├── remediation.md
├── report.md
├── screenshots.md
└── screenshots/
```

---

## Supporting Documentation

- **Findings:** `findings.md`
- **Remediation:** `remediation.md`
- **Assessment Report:** `report.md`
- **Evidence:** `screenshots.md`

---

## Learning Outcomes

This assessment provided practical experience in:

- Identifying reflected XSS vulnerabilities.
- Understanding how untrusted input is reflected into HTML responses.
- Using Burp Suite to intercept and modify HTTP requests.
- Evaluating the security impact of client-side code execution.
- Producing professional vulnerability assessment documentation.

---

## References

- OWASP Top 10 2021 – A03: Injection
- OWASP Cross Site Scripting (XSS) Prevention Cheat Sheet
- CWE-79: Improper Neutralization of Input During Web Page Generation ('Cross-site Scripting')

---

## Disclaimer

This assessment was conducted **only within an authorized DVWA laboratory environment** for educational purposes. All testing was performed against an intentionally vulnerable application running in a local virtual machine. No unauthorized systems or production environments were targeted.
