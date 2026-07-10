# SQL Injection Evidence

## 01-security-level

Shows DVWA configured with Low Security.

![Security Level](screenshots/01-security-level.png)

---

## 02-normal-request

Shows normal application response for User ID = 1.

![Normal Request](screenshots/02-normal-request.png)

---

## 03-burp-proxy-request

Captured request before manipulation.

![Burp Proxy](screenshots/03-burp-proxy-request.png)

---

## 04-burp-repeater-sqli

SQL Injection payload executed successfully.

Returned multiple database records.

![SQL Injection](screenshots/04-burp-repeater-sqli.png)

---

## 05-view-source

Source code reveals direct insertion of user input into SQL query.

![Source Code](screenshots/05-view-source.png)

