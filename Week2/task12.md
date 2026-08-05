# Task 12 – Backup Automation

## Objective

Create an automated backup solution.

---

## Commands Used

```bash
#!/bin/bash

# Check if a directory is provided
if [ $# -ne 1 ]; then
    echo "Usage: $0 <directory_to_backup>"
    exit 1
fi

SOURCE_DIR="$1"

# Verify the source directory exists
if [ ! -d "$SOURCE_DIR" ]; then
    echo "Error: Directory '$SOURCE_DIR' does not exist."
    exit 1
fi

# Backup directory
BACKUP_DIR="$HOME/backups"

# Log file
LOG_FILE="$BACKUP_DIR/backup.log"

# Create backup directory if it doesn't exist
mkdir -p "$BACKUP_DIR"

# Current timestamp
TIMESTAMP=$(date +"%Y-%m-%d_%H-%M-%S")

# Source directory name
DIR_NAME=$(basename "$SOURCE_DIR")

# Backup filename
BACKUP_FILE="$BACKUP_DIR/${DIR_NAME}_${TIMESTAMP}.tar.gz"

# Create compressed backup
tar -czf "$BACKUP_FILE" "$SOURCE_DIR"

# Check if backup was successful
if [ $? -eq 0 ]; then
    echo "$(date '+%Y-%m-%d %H:%M:%S') - Backup created: $BACKUP_FILE" >> "$LOG_FILE"
    echo "Backup successful: $BACKUP_FILE"
else
    echo "$(date '+%Y-%m-%d %H:%M:%S') - Backup failed for: $SOURCE_DIR" >> "$LOG_FILE"
    echo "Backup failed."
    exit 1
fi

# Remove backups older than 7 days
find "$BACKUP_DIR" -name "*.tar.gz" -type f -mtime +7 -exec rm -f {} \;

# Log cleanup operation
echo "$(date '+%Y-%m-%d %H:%M:%S') - Old backups older than 7 days removed." >> "$LOG_FILE"
```

---

## Explanation

### 1. Check for Input Directory

```bash
if [ $# -ne 1 ]; then
    echo "Usage: $0 <directory_to_backup>"
    exit 1
fi
```

**Explanation:**

* Verifies that exactly one directory path is provided as an argument.
* Displays the correct usage and exits if no input is given.

---

### 2. Store the Source Directory

```bash
SOURCE_DIR="$1"
```

**Explanation:**

* Stores the first command-line argument in the `SOURCE_DIR` variable.
* This directory will be backed up.

---

### 3. Verify the Directory Exists

```bash
if [ ! -d "$SOURCE_DIR" ]; then
    echo "Error: Directory '$SOURCE_DIR' does not exist."
    exit 1
fi
```

**Explanation:**

* Checks whether the specified directory exists.
* Stops execution if the directory is invalid.

---

### 4. Define Backup and Log Locations

```bash
BACKUP_DIR="$HOME/backups"
LOG_FILE="$BACKUP_DIR/backup.log"
```

**Explanation:**

* Defines a separate directory for storing backups.
* Specifies the log file where backup operations are recorded.

---

### 5. Create the Backup Directory

```bash
mkdir -p "$BACKUP_DIR"
```

**Explanation:**

* Creates the backup directory if it does not already exist.
* The `-p` option prevents errors if the directory is already present.

---

### 6. Generate a Timestamp

```bash
TIMESTAMP=$(date +"%Y-%m-%d_%H-%M-%S")
```

**Explanation:**

* Retrieves the current date and time.
* Ensures each backup filename is unique.

---

### 7. Get the Source Directory Name

```bash
DIR_NAME=$(basename "$SOURCE_DIR")
```

**Explanation:**

* Extracts only the directory name from the full path.
* Used when naming the backup file.

---

### 8. Create the Backup Filename

```bash
BACKUP_FILE="$BACKUP_DIR/${DIR_NAME}_${TIMESTAMP}.tar.gz"
```

**Explanation:**

* Creates a backup filename containing:

  * Source directory name
  * Current timestamp
  * `.tar.gz` extension

---

### 9. Create the Compressed Backup

```bash
tar -czf "$BACKUP_FILE" "$SOURCE_DIR"
```

**Explanation:**

* `tar` creates an archive.
* `-c` creates a new archive.
* `-z` compresses the archive using **gzip**.
* `-f` specifies the output filename.

---

### 10. Verify Backup Status

```bash
if [ $? -eq 0 ]; then
    ...
else
    ...
fi
```

**Explanation:**

* Checks the exit status of the `tar` command.
* Logs either a successful backup or a failure message.

---

### 11. Remove Old Backups

```bash
find "$BACKUP_DIR" -name "*.tar.gz" -type f -mtime +7 -exec rm -f {} \;
```

**Explanation:**

* Searches for backup files in the backup directory.
* Deletes files older than **7 days**.
* Prevents unnecessary storage usage.

---

### 12. Log Cleanup Operation

```bash
echo "$(date '+%Y-%m-%d %H:%M:%S') - Old backups older than 7 days removed." >> "$LOG_FILE"
```

**Explanation:**

* Records the cleanup activity in the backup log.
* Maintains a history of backup and maintenance operations.

---

