# Command Injection Screenshots

## 1. Normal Application Response

Shows the default application behavior when a valid IP address is submitted.

![Normal Ping](screenshots/command-injection/01-normal-ping.png)

---

## 2. Burp HTTP POST Request

Burp Suite intercepting the POST request.

![POST Request](screenshots/command-injection/02-burp-intercept-post-request.png)

---

## 3. Original Request in Repeater

Original POST request before modification.

![Repeater Original](screenshots/command-injection/03-repeater-original-request.png)

---

## 4. Successful Command Injection

The payload executes the `whoami` command.

![Whoami](screenshots/command-injection/04-command-injection-whoami.png)

---

## 5. Reading /etc/passwd

Sensitive file disclosure via command injection.

![Passwd](screenshots/command-injection/cmd_05_sensitive_file_read_passwd.png)

---

## 6. Netcat Listener

Attacker machine waiting for the reverse shell.

![Netcat Listener](screenshots/command-injection/06-netcat-listener.png)

---

## 7. Reverse Shell Established

Reverse shell successfully obtained.

![Reverse Shell](screenshots/command-injection/07-reverse-shell-established.png)
