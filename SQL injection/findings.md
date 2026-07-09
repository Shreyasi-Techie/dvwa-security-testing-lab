# SQL Injection

## Severity

High

## OWASP

A03:2021 Injection

## CVSS

8.8 High

---

## Description

The SQL query is constructed using user supplied input without proper validation.

This allows attackers to modify the SQL statement and retrieve unauthorized information.

---

## Payload

```sql
1' OR '1'='1
```

---

## Result

Instead of returning one user, the application disclosed multiple database records.

Users returned:

- admin
- Gordon Brown
- Hack Me
- Pablo Picasso
- Bob Smith

---

## Impact

- Database Enumeration
- Sensitive Information Disclosure
- Authentication Bypass
- Privilege Escalation
