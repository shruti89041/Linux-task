# Task 8 – Bash Automation


## Objective

Develop a reusable shell script.

---

## Commands Used

### 1. Create a Shell Script

```bash
nano directory_report.sh
```

**Explanation:**

- nano opens the Nano text editor.
- Creates a new shell script named directory_report.sh.

---

### 2. Write the Bash Script

```bash
#!/bin/bash

# Check if a directory is provided
if [ $# -ne 1 ]; then
    echo "Usage: $0 <directory>"
    exit 1
fi

DIR="$1"

# Check if the directory exists
if [ ! -d "$DIR" ]; then
    echo "Error: Directory does not exist."
    exit 1
fi

REPORT="directory_report.txt"

FILE_COUNT=$(find "$DIR" -type f | wc -l)
DIR_COUNT=$(find "$DIR" -type d | wc -l)
TOTAL_SIZE=$(du -sh "$DIR" | cut -f1)
LARGEST_FILE=$(find "$DIR" -type f -exec ls -lhS {} + 2>/dev/null | head -n 1 | awk '{print $9, $5}')

{
echo "===== Directory Report ====="
echo "Directory: $DIR"
echo "Date: $(date)"
echo "----------------------------"
echo "Total Files: $FILE_COUNT"
echo "Total Directories: $DIR_COUNT"
echo "Directory Size: $TOTAL_SIZE"
echo "Largest File: $LARGEST_FILE"
} > "$REPORT"

cat "$REPORT"
```

**Explanation:**

- Checks whether the user provides exactly one directory as input.
- Verifies that the specified directory exists.
- Counts files using find.
- Counts directories using find.
- Calculates the total directory size using du.
- Finds the largest file using find, ls, head, and awk.
- Saves the results to directory_report.txt.
- Displays the report on the terminal.

---

### 3. Make the Script Executable

```bash
chmod +x directory_report.sh
```

**Explanation:**

- chmod +x grants execute permission to the script.
---

### 4. Execute the Script

```bash
./directory_report.sh /home/shruti
```

**Explanation:**

- Runs the script and passes the target directory as an argument.

---

### 5. View the Generated Report

```bash
cat directory_report.txt
```

**Explanation:**

- Displays the contents of the generated report file.

---




