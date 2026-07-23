# Task 1 – User and Group Management

## Objective

Perform user and group administration using Linux commands by creating users and groups, managing memberships, configuring password policies, and verifying the configurations.

---

## Commands Used

### 1. Create a User

```bash
sudo useradd -m devopsintern
```

**Explanation:**

- `useradd` creates a new user account.
- `-m` creates a home directory for the user (`/home/devopsintern`).

---

### 2. Create a Group

```bash
sudo groupadd developers
```

**Explanation:**

- `groupadd` creates a new Linux group named **developers**.

---

### 3. Add the User to the Group

```bash
sudo usermod -aG developers devopsintern
```

**Explanation:**

- `usermod` modifies an existing user.
- `-a` appends the user to the supplementary group.
- `-G` specifies the supplementary group.
- This command adds **devopsintern** to the **developers** group without removing existing group memberships.

---

### 4. Set a Password for the User

```bash
sudo passwd devopsintern
```

**Explanation:**

- Assigns or changes the password for the user.
- Required before the user can log in.

---

### 5. Configure Password Expiry

```bash
sudo chage --maxdays 30 devopsintern
```

**Explanation:**

- `chage` changes password aging information.
- `--maxdays 30` sets the maximum password validity to **30 days**.

---

### 6. Force Password Change on First Login

```bash
sudo chage -d 0 devopsintern
```

**Explanation:**

- `-d 0` sets the last password change date to **0**.
- The user is required to change the password during the first login.

---



