# Task 11 – Linux Troubleshooting

## Objective

Investigate and troubleshoot common Linux issues.

---

# Scenario 1 – A Service Fails to Start

## Symptoms

* The service does not start after executing the start command.
* Users are unable to access the application or service.
* The service status displays **failed**.

### Investigation Steps

1. Check the service status.
2. Review the system logs for errors.
3. Verify the service configuration.
4. Restart the service after correcting the issue.

### Commands Used

Check service status:

```bash
sudo systemctl status nginx
```

View service logs:

```bash
sudo journalctl -u nginx
```

Restart the service:

```bash
sudo systemctl restart nginx
```

Enable service at boot:

```bash
sudo systemctl enable nginx
```

### Root Cause

* Invalid configuration.
* Port conflict.
* Missing configuration file.
* Required dependency not running.

### Resolution

* Correct the service configuration.
* Resolve the port conflict.
* Restart the service.

### Verification

```bash
sudo systemctl status nginx
```

Expected Result:

```text
Active: active (running)
```

---

# Scenario 2 – Disk Space is Almost Full

## Symptoms

* "No space left on device" errors.
* Unable to save files.
* Applications fail to write data.
* System performance decreases.

### Investigation Steps

1. Check overall disk usage.
2. Identify large directories.
3. Find large files.
4. Remove unnecessary files.
5. Clear package cache and logs.

### Commands Used

Check disk usage:

```bash
df -h
```

Check directory sizes:

```bash
du -sh /*
```

Find large files:

```bash
find / -type f -size +100M
```

Remove unused packages:

```bash
sudo apt autoremove
```

Clean package cache:

```bash
sudo apt clean
```

### Root Cause

* Large log files.
* Unused packages.
* Temporary files.
* Old backups consuming storage.

### Resolution

* Delete unnecessary files.
* Remove unused packages.
* Clear package cache.
* Archive or remove old backups.

### Verification

```bash
df -h
```

Expected Result:

* Available disk space has increased.

---

# Scenario 3 – SSH Login Fails

## Symptoms

* SSH connection is refused.
* Authentication fails.
* Remote login is unsuccessful.

### Investigation Steps

1. Verify the SSH service status.
2. Check whether SSH is listening on port 22.
3. Review SSH configuration.
4. Inspect authentication logs.
5. Confirm firewall rules.

### Commands Used

Check SSH service:

```bash
sudo systemctl status ssh
```

Restart SSH:

```bash
sudo systemctl restart ssh
```

Check listening ports:

```bash
ss -tulpn | grep ssh
```

View SSH configuration:

```bash
sudo cat /etc/ssh/sshd_config
```

Check authentication logs:

```bash
sudo journalctl -u ssh
```

Test SSH connection:

```bash
ssh username@server_ip
```

### Root Cause

* SSH service stopped.
* Incorrect SSH configuration.
* Firewall blocking port 22.
* Incorrect username or password.
* SSH daemon not listening.

### Resolution

* Start or restart the SSH service.
* Correct the SSH configuration.
* Allow port 22 through the firewall.
* Verify user credentials.
* Restart the SSH daemon.

### Verification

```bash
sudo systemctl status ssh
```

```bash
ssh username@server_ip
```

Expected Result:

* SSH connection is established successfully.

---

