# Task 7 –  File Compression and Archiving


## Objective

Understand Linux backup and archival utilities.
---

## Commands Used

### 1. Create a Sample Directory with Multiple Files

```bash
mkdir -p backup_demo
cd backup_demo

echo "This is file 1" > file1.txt
echo "This is file 2" > file2.txt
echo "This is file 3" > file3.txt
mkdir docs
echo "Sample document" > docs/doc1.txt


```

**Explanation:**

- mkdir -p creates the required directory.
- echo writes sample content into files.

---

### 2. Archive the Directory

```bash
tar -cvf backup.tar backup_demo
```

**Explanation:**

- tar creates and manages archive files.
---

### 3. Compress the Archive Using Gzip

```bash
gzip backup.tar
```

**Explanation:**

- gzip compresses the archive.
- The output file is backup.tar.gz
---

### 4. Compress the Archive Using Bzip2

```bash
tar -cvjf backup.tar.bz2 backup_demo
```

**Explanation:**

- -j applies bzip2 compression.
- Produces backup.tar.bz2

---

### 5. Compress the Archive Using XZ

```bash
tar -cvJf backup.tar.xz backup_demo
```

**Explanation:**

- -J applies XZ compression.
- Produces backup.tar.xz.
---

### 6. Extract the Archive into Another Directory

```bash
mkdir extracted_files
tar -xvf backup.tar.gz -C extracted_files

```

**Explanation:**

- mkdir creates the destination directory.
- -x extracts the archive.
- -v displays extracted files.
- -f specifies the archive file.
- -C extracts the files into the specified directory.
---

### 7. Compare the Compressed File Sizes

```bash
ls -lh backup.tar.gz backup.tar.bz2 backup.tar.xz
```

**Explanation:**

- ls -lh displays file sizes in a human-readable format.
---

### 8. Verify That the Extracted Files Match the Original Files

```bash
diff -r backup_demo extracted_files/backup_demo

```

**Explanation:**

- diff compares files and directories.
- -r performs a recursive comparison.
---

