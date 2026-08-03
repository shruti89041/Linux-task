# Task 6 – Systemd Service Management

## Objective

Create and manage your own Linux service.

---

## Commands Used

### 1. Create a Directory for the Script

```bash
mkdir -p ~/scripts
```

**Explanation:**

- mkdir creates a new directory.
- -p creates the directory only if it does not already exist and creates parent directories if required.

---

### 2. Create the Shell Script

```bash
nano ~/scripts/time_logger.sh

#!/bin/bash

while true
do
    echo "$(date)" >> /tmp/time_logger.log
    sleep 10
done
```

Make the script executable:

chmod +x ~/scripts/time_logger.sh

**Explanation:**

- nano opens the file in the Nano text editor.
- #!/bin/bash specifies the Bash interpreter.
- while true creates an infinite loop.
- date displays the current system date and time.
- >> appends the output to the log file without overwriting existing data.
- sleep 10 pauses execution for 10 seconds between log entries.
- chmod +x grants execute permission to the script.

---

### 3. Create the Systemd Service File

```bash
sudo nano /etc/systemd/system/time_logger.service

[Unit]
Description=Time Logger Service
After=network.target

[Service]
Type=simple
ExecStart=/home/shruti/scripts/time_logger.sh
Restart=always
RestartSec=5
User=shruti

[Install]
WantedBy=multi-user.target
```

**Explanation:**

- Creates a custom systemd service unit file.
---

### 4. Reload Systemd Configuration

```bash
sudo systemctl daemon-reload
```

**Explanation:**

- Reloads the systemd manager configuration after creating or modifying service files.

---

### 5. Start the Service

```bash
sudo systemctl start time_logger.service
```

**Explanation:**

- Starts the time_logger service immediately.
---

### 6. Check the Service Status

```bash
sudo systemctl status time_logger.service
```

**Explanation:**

- Displays the current status of the service, including whether it is running successfully.

---

### 7. Enable the Service at Boot

```bash
sudo systemctl enable time_logger.service
```

**Explanation:**

- Configures the service to start automatically whenever the system boots.

---

### 8. Verify the Log File

```bash
cat /tmp/time_logger.log
```

**Explanation:**

- Displays the contents of the log file to verify that the script is continuously appending the current date and time.

