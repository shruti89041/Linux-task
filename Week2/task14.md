# Task 14 – Linux Security and Permissions Audit

## Objective

Perform a basic Linux security audit.

---

## Commands Used

### 1. Find Files with SUID Permission

```bash
find / -type f -perm -4000 2>/dev/null
```

**Explanation:**

- find / searches the entire filesystem.
- -type f searches only for regular files.
- -perm -4000 identifies files with the SUID (Set User ID) permission.
- 2>/dev/null suppresses permission denied error messages.
---

### 2. Find Files with SGID Permission

```bash
find / -type f -perm -2000 2>/dev/null
```

**Explanation:**

- Searches for regular files with the SGID (Set Group ID) permission.
- SGID allows a program to run with the privileges of the file's group owner.
- Error messages are redirected to /dev/null.
---

### 3. Find World-Writable Files

```bash
find / -type f -perm -0002 2>/dev/null
```

**Explanation:**

- Searches for regular files that are writable by all users.
- -perm -0002 identifies files with the world-writable permission.
- These files may pose a security risk if not properly managed.

---

### 4. Find Empty Files

```bash
find / -type f -empty 2>/dev/null
```

**Explanation:**

- -empty searches for files with a size of 0 bytes.
- Useful for identifying unused or incomplete files.

---

### 5. Find Empty Directories

```bash
find / -type d -empty 2>/dev/null
```

**Explanation:**

- -type d limits the search to directories.
- -empty finds directories that contain no files or subdirectories.
- Helps identify unused directories that can be cleaned up.

---

### 6. Find Broken Symbolic Links

```bash
find / -xtype l 2>/dev/null
```

**Explanation:**

- -xtype l finds symbolic links whose target files no longer exist.
- Broken symbolic links should be removed or corrected to avoid system confusion.
---


