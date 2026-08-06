# Task 15 – Mini Linux Administration Project


---

## Objective

Apply all Linux concepts learned during Weeks 1 and 2.

---


## Architecture

```
                    +----------------------+
                    |      Client PC       |
                    | (SSH/Web Browser)    |
                    +----------+-----------+
                               |
                    SSH (22) / HTTP (80)
                               |
                 +-------------+-------------+
                 |      Linux Server         |
                 |                           |
                 |  Users & Groups           |
                 |  SSH Key Authentication   |
                 |  Nginx Web Server         |
                 |  Systemd Service          |
                 |  Cron Scheduler           |
                 |  Backup Script            |
                 +---------------------------+
```

---


## User and Group Management

Created users:

- developer1
- developer2

Created groups:

- developers
- admins

Example commands:

```bash
sudo useradd -m developer1
sudo useradd -m developer2

sudo groupadd developers
sudo groupadd admins

sudo usermod -aG developers developer1
sudo usermod -aG admins developer2
```

---

## File Permissions

Created a shared project directory.

```bash
sudo mkdir /project
sudo chown developer1:developers /project
sudo chmod 770 /project
```

---

## Nginx Installation

Install Nginx.

```bash
sudo apt update
sudo apt install nginx -y
```

Enable and start the service.

```bash
sudo systemctl enable nginx
sudo systemctl start nginx
```

Create a simple web page.

```bash
echo "<h1>Welcome to My Linux Server</h1>" | sudo tee /var/www/html/index.html
```

---

## Custom Systemd Service

Service file:

`/etc/systemd/system/helloservice.service`

```ini
[Unit]
Description=Custom Hello Service

[Service]
ExecStart=/bin/bash -c 'while true; do echo "Hello from Systemd"; sleep 60; done'

[Install]
WantedBy=multi-user.target
```

Enable the service.

```bash
sudo systemctl daemon-reload
sudo systemctl enable helloservice
sudo systemctl start helloservice
```

---

## Backup Script

Create `backup.sh`

```bash
#!/bin/bash

tar -czf /home/developer1/backup-$(date +%F).tar.gz /project
```

Make executable.

```bash
chmod +x backup.sh
```

---

## Cron Job

Schedule automatic backups every day at 2:00 AM.

```cron
0 2 * * * /home/developer1/backup.sh
```

View cron jobs.

```bash
crontab -l
```

---

## SSH Key Authentication

Generate SSH keys.

```bash
ssh-keygen -t rsa -b 4096
```

Copy the public key.

```bash
ssh-copy-id developer1@server-ip
```

(Optional)

Disable password authentication.

```text
PasswordAuthentication no
PubkeyAuthentication yes
```

Restart SSH.

```bash
sudo systemctl restart ssh
```

---

## Verification

Verify users.

```bash
cat /etc/passwd | grep developer
```

Verify groups.

```bash
groups developer1
groups developer2
```

Verify permissions.

```bash
ls -ld /project
```

Verify Nginx.

```bash
systemctl status nginx
```

Open in browser.

```
http://server-ip
```

Verify systemd service.

```bash
systemctl status helloservice
```

Verify cron.

```bash
crontab -l
```

Verify backup.

```bash
ls /home/developer1/*.tar.gz
```

Verify SSH.

```bash
ssh developer1@server-ip
```

---

## Testing After Reboot

Reboot the server.

```bash
sudo reboot
```

Verify:

```bash
systemctl status nginx
systemctl status helloservice

crontab -l
```

Open:

```
http://server-ip
```

The website should be accessible, and all configured services should start automatically.


---

## Learning Outcomes

This project demonstrates the following Linux administration skills:

- User and group management
- Linux file permissions
- Service management using systemd
- Web server configuration with Nginx
- Cron job scheduling
- Shell scripting
- Backup automation
- SSH key authentication
- Linux system verification and troubleshooting

---

## Conclusion

The Linux server was successfully configured with secure user management, proper permissions, web hosting, automated backups, scheduled tasks, and SSH key authentication. All configurations persist across system reboots, demonstrating a reliable and maintainable Linux administration setup.
