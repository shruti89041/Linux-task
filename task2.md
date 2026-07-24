# Task 2 – Linux Permissions

## Objective

Objective
Understand ownership and permission management.
Create the following directory structure:
company/
├── developers/
├── testers/
└── shared/

Configure permissions so that:
Developers can access only the developers directory.
Testers can access only the testers directory.
Both groups can access the shared directory.
Other users should not have access.

---

## Commands Used

### 1. Create the Directory Structure

```bash
mkdir -p company/{developers,testers,shared}

```

**Explanation:**

-mkdir creates directories.
-p creates parent directories if they do not exist and avoids errors if the directories already exist.
The brace expansion {developers,testers,shared} creates the three subdirectories (developers, testers, and shared) inside the company directory.

---

### 2. Create the Required Groups

```bash
sudo groupadd developers
sudo groupadd testers
sudo groupadd sharedgrp

```

**Explanation:**

- groupadd creates a new Linux group.
developers is used for users who need access to the developers directory.
testers is used for users who need access to the testers directory.
sharedgrp is used to grant both developers and testers access to the shared directory.
---

### 3. Assign Group Ownership

```bash
sudo chown root:developers company/developers
sudo chown root:testers company/testers
sudo chown root:sharedgrp company/shared

```

**Explanation:**

- chown changes the ownership of a file or directory.
root is set as the owner of each directory.
The group ownership is assigned as follows:
developers for the developers directory.
testers for the testers directory.
sharedgrp for the shared directory.
---

