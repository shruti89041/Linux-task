# Task 8 –  Linux Environment and Shell Configuration

## Objective

Understand the Linux shell environment.
---

## Commands Used

### 1. Display All Environment Variables

```bash
printenv
```

**Explanation:**

- printenv displays all current environment variables.
---

### 2. Create a Custom Environment Variable

```bash
export MY_VARIABLE="Hello Linux"
```

**Explanation:**

- export creates an environment variable that is available to the current shell and its child processes.
- MY_VARIABLE is the variable name.
- "Hello Linux" is the assigned value.
---

### 3. Make the Variable Persistent Across Login Sessions

```bash
echo 'export MY_VARIABLE="Hello Linux"' >> ~/.bashrc
source ~/.bashrc

```

**Explanation:**

- ~/.bashrc stores user-specific shell configuration.
- Adding the export command makes the variable available every time a new shell session starts.
- source ~/.bashrc reloads the configuration without logging out.
---

### 4. Configure a Custom Shell Alias

```bash
alias ll='ls -alF'
```

**Explanation:**

- alias creates a shortcut for a command.
- ll becomes a shortcut for ls -alF, which displays a detailed directory listing
---

### 5. Display Your Current Shell

```bash
echo $SHELL
```

### 6. Display the Current PATH Variable

```bash
echo $PATH

```

### 7. Modify the PATH Variable

```bash
export PATH=$PATH:/home/$USER/scripts
```

**Explanation:**

- Appends /home/$USER/scripts to the existing PATH.
- Commands stored in this directory can now be executed without specifying the full path.
- This change is temporary and lasts only for the current shell session.
---

