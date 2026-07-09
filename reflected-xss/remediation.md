# Remediation

The application should never reflect raw user input into HTML.

Recommended controls

- Validate user input
- Encode output before rendering
- Use Content Security Policy (CSP)
- Mark cookies as HttpOnly
- Sanitize HTML content
- Use secure development frameworks

Example

Unsafe

```php
echo $_GET['name'];
```

Safe

```php
echo htmlspecialchars($_GET['name'], ENT_QUOTES, 'UTF-8');
```
