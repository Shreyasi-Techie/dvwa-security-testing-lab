# Command Injection Screenshots

## 1. Normal Application Response

**File:** `01-normal-ping.png`

Shows the default application behavior when a valid IP address (127.0.0.1) is submitted.

---

## 2. HTTP POST Request Captured

**File:** `02-burp-intercept-post-request.png`

Burp Suite intercepting the HTTP POST request sent to the vulnerable endpoint.

---

## 3. Original Request in Burp Repeater

**File:** `03-repeater-original-request.png`

Original POST request containing the user-controlled `ip` parameter before modification.

---

## 4. Successful Command Injection

**File:** `04-command-injection-whoami.png`

The payload appended an operating system command to the IP parameter.

The response contains:

- Ping output
- Username (`www-data`)

confirming arbitrary command execution.

---

## 5. Reading Sensitive Files

**File:** `05-sensitive-file-read-passwd.png`

The injected command displayed the contents of `/etc/passwd`, demonstrating the ability to access sensitive files.

---

## 6. Netcat Listener

**File:** `06-netcat-listener.png`

Attacker machine waiting for an incoming reverse shell connection.

---

## 7. Reverse Shell Established

**File:** `07-reverse-shell-established.png`

Successful reverse shell connection obtained.

Executed commands include:

- whoami
- hostname
- ls

confirming remote command execution on the vulnerable server.
