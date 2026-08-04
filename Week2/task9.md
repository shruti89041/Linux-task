# Task 9 – Package Management

## Objective

The objective of this task is to understand Linux package management by installing, verifying, and removing software packages using the `apt` package manager. This task also explains the differences between `apt`, `dpkg`, and `snap`, and identifies when each package manager should be used.

---

## Prerequisites

* Ubuntu/Debian-based Linux system
* User account with `sudo` privileges
* Internet connection

---

## Packages Installed

* Nginx
* Git
* Curl

---

## Installation Steps

### Update the Package Repository

```bash
sudo apt update
```

### Install Nginx

```bash
sudo apt install nginx -y
```

### Install Git

```bash
sudo apt install git -y
```

### Install Curl

```bash
sudo apt install curl -y
```

---

## Verify Installation

### Verify Nginx

```bash
nginx -v
```

### Verify Git

```bash
git --version
```

### Verify Curl

```bash
curl --version
```

Successful execution of these commands confirms that the packages have been installed correctly.

---

## Remove Installed Packages

### Remove the Packages

```bash
sudo apt remove nginx git curl -y
```

### Remove Configuration Files

```bash
sudo apt purge nginx git curl -y
```

### Remove Unused Dependencies

```bash
sudo apt autoremove -y
```

---

## Verify Cleanup

Run the following commands:

```bash
nginx -v
git --version
curl --version
```

If the packages have been removed successfully, the terminal will display a **"command not found"** message or indicate that the package is not installed.

---

## Package Manager Comparison

| Package Manager | Description                                                                                                                                           | Best Use Case                                                                            |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| **apt**         | High-level package manager that installs, updates, removes, and manages packages from online repositories while automatically resolving dependencies. | Everyday package installation and system updates on Debian/Ubuntu systems.               |
| **dpkg**        | Low-level package manager used for installing and managing local `.deb` packages. It does not resolve dependencies automatically.                     | Installing local `.deb` files or troubleshooting package-related issues.                 |
| **snap**        | Universal package manager that installs sandboxed applications with bundled dependencies across multiple Linux distributions.                         | Installing the latest versions of applications or software distributed as Snap packages. |

---

## Expected Outcome

After completing this task, you should be able to:

* Update package repositories.
* Install software packages using `apt`.
* Verify successful package installation.
* Remove packages and their configuration files.
* Clean unused dependencies.
* Understand the differences between `apt`, `dpkg`, and `snap`.
* Choose the appropriate package manager based on the installation scenario.

---

## Conclusion

This task provides practical experience with Linux package management by demonstrating the complete lifecycle of software installation, verification, removal, and cleanup. It also highlights the roles of `apt`, `dpkg`, and `snap` in managing software on Linux systems.
