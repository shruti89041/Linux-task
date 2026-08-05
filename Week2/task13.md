# Task 13 – SSH Configuration and Security


## Objective

Configure SSH securely.


---

## Commands Used

### 1. Disable Root Login

```bash
sudo nano /etc/ssh/sshd_config

PermitRootLogin no

sudo systemctl restart ssh
```

**Explanation:**

- PermitRootLogin no prevents users from logging in directly as the root user.

---

### 2. Configure Key-Based Authentication

```bash
ssh-keygen -t rsa -b 4096
```

**Explanation:**

- ssh-keygen generates a public/private SSH key pair.
---

### 3. Disable Password Authentication

```bash
sudo nano /etc/ssh/sshd_config
PasswordAuthentication no
```

**Explanation:**

- Disables password-based logins.
- Only users with valid SSH keys can access the server.
---

### 4. Change the Default SSH Port

```bash
sudo nano /etc/ssh/sshd_config

Port 2222
```

**Explanation:**

- Changes the SSH service from the default port 22 to 2222.

---

### 5. Verify SSH Login

```bash
ssh -p 2222 username@server_ip

```

**Explanation:**

- -p 2222 specifies the new SSH port.

---

**Why These Changes Improve Security**
* Disabling root login prevents attackers from directly targeting the root account.
* Key-based authentication is much more secure than passwords because private keys are difficult to guess or brute-force.
* Disabling password authentication eliminates password-based attacks such as brute-force and dictionary attacks.
* Changing the default SSH port reduces automated scanning and unauthorized login attempts from bots targeting port 22.

**Possible Risks of Incorrect SSH Configuration**
- Disabling password authentication before configuring SSH keys can lock administrators out of the server.
- Changing the SSH port without updating firewall rules can prevent remote access.
- Restarting the SSH service with an incorrect configuration may cause the service to fail.
