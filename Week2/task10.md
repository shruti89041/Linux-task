# Task 10 – Linux Networking

## Objective

Investigate and understand Linux networking.

---

## Commands Used

### Display Private IP Address

```bash
ip addr show
```

**Alternative**

```bash
hostname -I
```

Displays the IP address assigned to the local machine.

---

### Display Public IP Address

```bash
curl ifconfig.me
```

Retrieves the public IP address assigned by the Internet Service Provider (ISP).

---

### Display Default Gateway

```bash
ip route
```

Shows the routing table. The line beginning with `default via` indicates the default gateway.

---

### Display DNS Server

```bash
cat /etc/resolv.conf
```

Displays the configured DNS server(s).

---

### Display Open Ports

```bash
ss -tuln
```

Lists all listening TCP and UDP ports.

---

### Display Listening Services

```bash
sudo ss -tulpn
```

Displays listening ports together with the associated process names and process IDs.

---



## Network Information Collected

| Information        | Command                |
| ------------------ | ---------------------- |
| Private IP Address | `ip addr show`         |
| Public IP Address  | `curl ifconfig.me`     |
| Default Gateway    | `ip route`             |
| DNS Server         | `cat /etc/resolv.conf` |
| Open Ports         | `ss -tuln`             |
| Listening Services | `sudo ss -tulpn`       |

---

## Comparison of Networking Tools

### `ss` vs `netstat`

| ss                                               | netstat                         |
| ------------------------------------------------ | ------------------------------- |
| Modern socket statistics utility                 | Legacy networking utility       |
| Faster and more efficient                        | Slower on large systems         |
| Installed by default on most Linux distributions | Part of the `net-tools` package |
| Recommended replacement for `netstat`            | Mostly used on older systems    |

---

### `ping` vs `traceroute`

| ping                                | traceroute                                  |
| ----------------------------------- | ------------------------------------------- |
| Tests network connectivity          | Displays the route packets follow           |
| Measures latency                    | Identifies each router (hop)                |
| Uses ICMP Echo Requests             | Uses UDP or ICMP with increasing TTL values |
| Detects whether a host is reachable | Diagnoses routing issues                    |

---

### TCP vs UDP

| TCP                               | UDP                                   |
| --------------------------------- | ------------------------------------- |
| Connection-oriented               | Connectionless                        |
| Reliable data delivery            | Best-effort delivery                  |
| Error checking and retransmission | No retransmission                     |
| Slower due to reliability         | Faster with lower overhead            |
| Used for HTTP, HTTPS, FTP, SSH    | Used for DNS, VoIP, Streaming, Gaming |

---
