# Reflected Cross-Site Scripting (XSS) Findings

## Vulnerability Summary

A Reflected Cross-Site Scripting (XSS) vulnerability was identified in the Damn Vulnerable Web Application (DVWA) at the **Low** security level.

The application reflects user-supplied input directly into the HTML response without performing proper input validation or output encoding. As a result, arbitrary JavaScript can be executed within the victim's browser.

---

## Vulnerability Details

| Field | Value |
|-------|-------|
| Vulnerability | Reflected Cross-Site Scripting (XSS) |
| Severity | High |
| CVSS (Approx.) | 6.1 (Medium-High) |
| CWE | CWE-79 |
| OWASP Top 10 | A03:2021 – Injection |
| Affected Parameter | `name` |
| HTTP Method | GET |
| Application | DVWA |
| Security Level | Low |

---

## Affected Endpoint

```
GET /dvwa/vulnerabilities/xss_r/
```

Parameter:

```
name
```

---

## Description

The application accepts user-controlled input through the **name** parameter and reflects it back into the webpage without sanitization or HTML encoding.

Since the input is rendered directly into the HTML document, an attacker can inject malicious JavaScript that executes in the browser of any user visiting a crafted URL.

---

## Proof of Concept

### Normal Input

```
test
```

Output:

```
Hello test
```

---

### Payload 1

```html
<script>alert(1)</script>
```

Observed Behaviour

- JavaScript executed successfully.
- Browser displayed an alert dialog.
- Confirms arbitrary JavaScript execution.

---

### Payload 2

```html
<script>alert(document.cookie)</script>
```

Observed Behaviour

The browser displayed the current session cookies.

Example:

```
security=low
PHPSESSID=86fc35ab4f58735c903c3eff9d63270f
```

This demonstrates that client-side information can be accessed through injected JavaScript.

---

## Evidence Collected

The following evidence was collected during testing:

- Vulnerable webpage
- Burp Suite intercepted request
- Modified HTTP request
- Server response reflecting injected script
- Browser alert proving JavaScript execution
- Cookie disclosure proof
- Source code review showing unsanitized output

Supporting screenshots are available in the **screenshots/** directory.

---

## Impact

Successful exploitation could allow an attacker to:

- Execute arbitrary JavaScript in a victim's browser.
- Access non-HttpOnly cookies.
- Hijack authenticated sessions.
- Redirect users to malicious websites.
- Display fake login pages (phishing).
- Modify webpage content.
- Perform actions on behalf of authenticated users.

---

## Root Cause

The application directly inserts user-controlled input into the HTML response without performing:

- Input validation
- Output encoding
- HTML escaping

The vulnerable code prints the supplied parameter directly, allowing embedded JavaScript to execute.

---

## Risk Rating

**High**

Although this assessment was performed in a controlled laboratory environment (DVWA), the same coding pattern in a production application could result in session hijacking, credential theft, phishing attacks, and client-side code execution.

---

## References

- OWASP Cross Site Scripting (XSS)
- CWE-79: Improper Neutralization of Input During Web Page Generation
- OWASP Top 10 2021 – A03: Injection
