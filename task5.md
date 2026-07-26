# Task 5 – Linux Log Analysis

## Objective

Understand Linux logging.
Investigate:
Failed login attempts
System boot history
SSH login history
Last shutdown
Failed services
Explain:
Where Linux stores logs
Which commands were used
Why those commands were appropriate


---

## Commands Used

### 1. View Failed Login Attempts

```bash
sudo lastb
```

**Explanation:**

- lastb displays failed login attempts recorded on the system

---

### 2. View System Boot History

```bash
last reboot
```

**Explanation:**

- last displays the login and reboot history.
- reboot filters the output to show only system boot events.

---

### 3. View SSH Login History

```bash
last
```

**Explanation:**

- last displays recent user login history.
---

### 4. View Last Shutdown Information

```bash
last -x | grep shutdown
```

**Explanation:**

- last -x displays system shutdown and run-level changes.
- grep shutdown filters the output to display only shutdown events.

---

### 5. View Failed Services

```bash
systemctl --failed
```

### 6. Where Linux Stores Logs

- /var/log/syslog	: General system logs (Ubuntu/Debian).
- /var/log/messages	: General system logs (RHEL/CentOS).
- /var/log/auth.log :	Authentication and SSH login logs (Ubuntu/Debian).
- /var/log/secure : 	Authentication logs (RHEL/CentOS).
- /var/log/wtmp	: Login and logout history.

