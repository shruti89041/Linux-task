# Task 6 –  File Search and Text Processing

## Objective

Learn how to efficiently search, filter, and analyze files using standard Linux utilities.
---

## Commands Used

### 1. Create a Sample Directory Structure

```bash
mkdir -p file_search/{logs,data,reports}
cd file_search

touch logs/app.log logs/system.log logs/error.log
touch data/users.txt data/info.txt
touch reports/report.txt

```

**Explanation:**

- mkdir -p creates the required directory structure.
- touch creates empty files for testing.

---

### 2. Create a Large File (More Than 100 MB)

```bash
fallocate -l 120M logs/big.log
```

**Explanation:**

- fallocate creates a file of the specified size.
- -l 120M allocates a file of 120 MB.
---

### 3. Find All .log Files

```bash
find . -type f -name "*.log"
```

**Explanation:**

- find searches for files and directories.
-type f limits the search to regular files.
-name "*.log" finds files with the .log extension.
---

### 4. Find Files Larger Than 100 MB

```bash
find . -type f -size +100M
```

**Explanation:**

- -size +100M searches for files larger than 100 MB.

---

### 5. Search for a Specific Word Inside All Files

```bash
grep -r "ERROR" .
```

**Explanation:**

- grep searches for text within files.
- -r performs a recursive search through all files and subdirectories.
- "ERROR" is the search keyword.
---

### 6. Count the Number of Occurrences of a Word

```bash
grep -ro "ERROR" . | wc -l

```

**Explanation:**

- grep -o prints each matching occurrence on a separate line.
 -r searches recursively.
- wc -l counts the number of matching lines, giving the total occurrences.

---

### 7. Display the First 20 Lines of a Large Log File

```bash
head -20 logs/big.log
```

**Explanation:**

- head displays the beginning of a file.
 -20 displays the first 20 lines.
---

### 8. Display the Last 20 Lines of a Large Log File

```bash
tail -20 logs/big.log

```

**Explanation:**

- tail displays the end of a file.
- -20 displays the last 20 lines.
---

### 9. Extract Only Unique Lines from a File

```bash
sort data/info.txt | uniq

```

**Explanation:**

- sort arranges the lines alphabetically.
- uniq removes consecutive duplicate lines.
