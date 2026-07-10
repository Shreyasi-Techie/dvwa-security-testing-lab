---

# Reflected Cross-Site Scripting (XSS)

## Vulnerability Overview

Reflected Cross-Site Scripting (XSS) occurs when user-supplied input is immediately returned in the application's response without proper validation or output encoding. This allows attackers to execute arbitrary JavaScript in the victim's browser.

| Property | Value |
|----------|-------|
| **Vulnerability Type** | Reflected Cross-Site Scripting (XSS) |
| **Severity** | High |
| **CVSS v3.1** | 6.1 |
| **Affected Module** | DVWA – Reflected XSS |

---

## Objective

To verify whether the application improperly reflects user input and allows execution of JavaScript code within the browser.

---

## Tools Used

- Kali Linux
- DVWA
- Burp Suite Community Edition
- Firefox Browser

---

## Methodology

1. Set DVWA Security Level to **Low**.
2. Open the **Reflected XSS** module.
3. Capture the HTTP request using Burp Suite.
4. Modify the `name` parameter with JavaScript payloads.
5. Forward the request.
6. Observe browser behavior and server response.

---

## Payloads Used

### Payload 1

```html
<script>alert(1)</script>
```

### Payload 2

```html
<script>alert(document.cookie)</script>
```

---

## Evidence

### Test 1 – JavaScript Execution

**Payload**

```html
<script>alert(1)</script>
```

**Result**

- JavaScript executed successfully.
- Browser displayed an alert box.
- User input was reflected without sanitization.

**Screenshot**

![](screenshots/xss-alert.png)

---

### Test 2 – Cookie Disclosure

**Payload**

```html
<script>alert(document.cookie)</script>
```

**Result**

- Browser displayed the session cookie.
- Demonstrates the possibility of session hijacking.

**Screenshot**

![](screenshots/xss-cookie.png)

---

### HTTP Request Analysis

Burp Suite intercepted the request containing the injected payload.

**Screenshot**

![](screenshots/xss-burp-request.png)

---

### HTTP Response Analysis

The server reflected the malicious script without encoding.

**Screenshot**

![](screenshots/xss-burp-response.png)

---

## Impact

Successful exploitation may allow an attacker to:

- Execute arbitrary JavaScript
- Steal session cookies
- Hijack authenticated sessions
- Redirect users to malicious websites
- Modify page contents

---

## Risk Rating

**High**

---

## Remediation

- Validate all user inputs.
- Encode output before rendering.
- Implement a Content Security Policy (CSP).
- Store session cookies with `HttpOnly` and `Secure` flags.
- Use modern templating frameworks with automatic output encoding.

---
