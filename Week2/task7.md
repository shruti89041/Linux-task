# Task 7 – Cron Job Scheduling

## Objective

Learn Linux task scheduling.

---

## Commands Used

### 1. Open the Crontab Editor

```bash
crontab -e
```

**Explanation:**

- crontab -e opens the current user's cron table in the default text editor.
- Used to create, edit, or remove scheduled cron jobs..

---

### 2. Schedule a Job to Run Every Minute

```bash
1 * * * * sh ~/test.sh
```

**Explanation:**

- The first * means every minute.
- The remaining * symbols indicate every hour, every day, every month, and every day of the week.
---

### 3. Schedule a Job to Run Every 15 Minutes

```bash
*/15 * * * * /home/shruti/comments.sh
```

**Explanation:**

- */15 means every 15 minutes (0, 15, 30, and 45).
- The remaining * symbols indicate every hour, every day, every month, and every day of the week.
---

### 4. Schedule a Job to Run Every Monday

```bash
0 9 * * 1 /home/shruti/comments.sh
```

**Explanation:**

- 0 specifies minute 0.
- 9 specifies 9 AM.
- * means every day of the month.
- * means every month.
- 1 represents Monday.
- Executes the script every Monday at 9:00 AM.

---

### 5. Schedule a Job on the First Day of Every Month

```bash
0 0 1 * * /home/shruti/comments.sh
```

**Explanation:**

- 0 specifies minute 0.
- 0 specifies hour 0 (midnight).
- 1 specifies the first day of the month.
- * means every month.
- * means every day of the week.
- Executes the script at 12:00 AM on the first day of every month.

---

### 6. Schedule a Job at System Startup

```bash
@reboot /home/shruti/comments.sh
```

**Explanation:**

- @reboot is a special cron keyword.
- Executes the specified script automatically whenever the system boots.

---

### 7. View Scheduled Cron Jobs

```bash
crontab -l
```

**Explanation:**

- Displays all cron jobs configured for the current user.
- Used to verify that the cron entries have been added successfully.

---

### 8. Check the Cron Service Status

```bash
sudo systemctl status cron
```

**Explanation:**

- Displays the current status of the cron service.
- Confirms whether the cron daemon is running.

---

### 9. Start the Cron Service (if Required)

```bash
sudo systemctl start cron
```

**Explanation:**

- Starts the cron service if it is not already running.

---
