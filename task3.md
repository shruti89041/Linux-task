# Task 3 – Process Management

## Objective

Understand Linux process management.

---

## Commands Used

### 1. Start multiple background processes

```bash
sleep 300 &
sleep 400 &
sleep 500 &
```

**Explanation:**

- sleep creates a process that runs for the specified number of seconds.
- & runs the process in the background, allowing the terminal to remain available for other commands.

---

### 2. View Running Processes

```bash
ps -ef

```

**Explanation:**

- ps displays information about running processes.
-e shows all processes.
-f displays detailed information such as PID, user, and start time.

---

### 3. Identify the Highest CPU-Consuming Process

```bash
ps -eo pid,comm,%cpu --sort=-%cpu | head
```

**Explanation:**

- -eo specifies the output columns.
--sort=-%cpu sorts processes in descending order of CPU usage.
head displays the top CPU-consuming processes.

---

### 4.Identify the Highest Memory-Consuming Process

```bash
ps -eo pid,comm,%mem --sort=-%mem | head
```

**Explanation:**

- Displays the process ID, command name, and memory usage.
--sort=-%mem sorts processes by memory usage in descending order.

---

### 5. Stop a Process Gracefully

```bash
kill <PID>
```

**Explanation:**

- Requests the specified process to terminate gracefully.

---

### 6. Restart the Process

```bash
sleep 300 &
```

**Explanation:**

- Starts the process again in the background.
A new Process ID (PID) is assigned.

---
### 6. SIGTERM: It requests a process to terminate gracefully.
Allows the process to save data, close files, and release system resources before exiting.
-
-SIGKILL (Signal 9): kill -9 <PID>

Explanation:

SIGKILL forcefully terminates a process.
-
Difference Between kill and pkill
kill	pkill
Uses the Process ID (PID) to terminate a process.	Pkill Uses the process name or matching criteria to terminate process(es).
Kill Requires the PID.	Pkill Does not require the PID.




