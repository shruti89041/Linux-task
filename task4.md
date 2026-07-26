# Task 3 – Process Management

## Objective

Disk Usage Investigation

---

## Commands Used

### 1. Create a Directory for Testing

```bash
mkdir storage-analysis
cd storage-analysis
```

**Explanation:**

- mkdir creates a new directory named storage_analysis
- cd changes the current working directory.

---

### 2. Create Files Totaling at Least 1 GB

```bash
fallocate -l 300M file1.img
fallocate -l 250M file2.img
fallocate -l 200M file3.img
fallocate -l 150M file4.img
fallocate -l 124M file5.img

```

**Explanation:**

- fallocate quickly allocates disk space for a file.
- -l specifies the size of the file.

---

### 3. Find the Top 10 Largest Files

```bash
find . -type f -exec du -h {} + | sort -hr | head -10
```

**Explanation:**

- find . -type f searches for all files in the current directory.
- du -h displays file sizes in a human-readable format.
- sort -hr sorts the files from largest to smallest.
- head -10 displays the top 10 largest files.

---

### 4.Find the Top 5 Largest Directories

```bash
du -h --max-depth=1 | sort -hr | head -5
```

**Explanation:**

- du -h shows the size of directories in a human-readable format.
- --max-depth=1 limits the output to the current directory and its immediate subdirectories.
- sort -hr sorts directories by size.
- head -5 displays the five largest directories.

---

### 5. Find Files Modified Within the Last 24 Hours

```bash
find . -mtime -1
```

**Explanation:**

- -mtime -1 finds files modified within the last 24 hours.

---

### 6. Find Files Owned by the Root User

```bash
sudo find / -user root
```

