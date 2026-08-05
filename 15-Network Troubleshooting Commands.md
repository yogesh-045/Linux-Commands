# 🌐 Day 15 - Network Troubleshooting Commands

Network troubleshooting commands help diagnose connectivity issues, verify DNS resolution, inspect network interfaces, identify active connections, and capture network traffic. These commands are widely used by SOC Analysts, Network Engineers, and Incident Responders.

---

# Commands Summary

| Command | Syntax | Description |
|---------|--------|-------------|
| `ping` | `ping hostname` | Tests network connectivity to a remote host. |
| `ss` | `ss` | Displays active network connections and listening ports. |
| `netstat` | `netstat -tuln` | Displays network connections, routing tables, and listening ports. |
| `dig` | `dig domain.com` | Queries DNS servers for domain information. |
| `nslookup` | `nslookup domain.com` | Retrieves DNS records for a domain. |
| `traceroute` | `traceroute hostname` | Displays the path packets take to reach a destination. |
| `arp` | `arp -a` | Displays the ARP cache. |
| `ip neigh` | `ip neigh` | Displays neighboring devices stored in the ARP table. |
| `tcpdump` | `tcpdump` | Captures and analyzes live network packets. |

---

# 1. ping

## Description

Tests whether a remote host is reachable over the network.

### Syntax

```bash
ping hostname
```

### Example

```bash
ping google.com
```

### SOC Analyst Use Case

Verify whether a server is reachable during incident investigation.

---

# 2. ss

## Description

Displays active TCP/UDP connections and listening ports.

### Syntax

```bash
ss
```

### Example

```bash
ss -tuln
```

### SOC Analyst Use Case

Identify suspicious listening ports or active network connections.

---

# 3. netstat

## Description

Displays network connections, routing tables, interface statistics, and listening ports.

### Syntax

```bash
netstat -tuln
```

### Example

```bash
netstat -an
```

### SOC Analyst Use Case

Detect malware communicating with external IP addresses.

---

# 4. dig

## Description

Queries DNS servers and displays DNS records.

### Syntax

```bash
dig domain.com
```

### Example

```bash
dig google.com
```

### SOC Analyst Use Case

Verify DNS resolution during phishing or malware investigations.

---

# 5. nslookup

## Description

Retrieves DNS information for a domain.

### Syntax

```bash
nslookup domain.com
```

### Example

```bash
nslookup google.com
```

### SOC Analyst Use Case

Check domain resolution during security investigations.

---

# 6. traceroute

## Description

Displays each network hop between your system and the destination.

### Syntax

```bash
traceroute hostname
```

### Example

```bash
traceroute google.com
```

### SOC Analyst Use Case

Identify where network communication is delayed or blocked.

---

# 7. arp

## Description

Displays the Address Resolution Protocol (ARP) cache.

### Syntax

```bash
arp -a
```

### Example

```bash
arp -a
```

### SOC Analyst Use Case

Identify IP-to-MAC address mappings during network investigations.

---

# 8. ip neigh

## Description

Displays neighboring devices from the ARP neighbor table.

### Syntax

```bash
ip neigh
```

### Example

```bash
ip neigh
```

### SOC Analyst Use Case

Verify devices communicating on the local network.

---

# 9. tcpdump

## Description

Captures and analyzes live network traffic.

### Syntax

```bash
tcpdump
```

### Example

```bash
sudo tcpdump -i eth0
```

Capture 10 packets:

```bash
sudo tcpdump -c 10
```

Save packets:

```bash
sudo tcpdump -w capture.pcap
```

### SOC Analyst Use Case

Capture suspicious network traffic for forensic analysis using Wireshark.

---

# Common SOC Analyst Commands

```bash
ping google.com

ss -tuln

netstat -an

dig google.com

nslookup google.com

traceroute google.com

arp -a

ip neigh

sudo tcpdump -i eth0
```

---

# Interview Questions

### 1. What is the purpose of the `ping` command?

**Answer:**

The `ping` command checks whether a remote host is reachable and measures network latency.

---

### 2. What is the difference between `ss` and `netstat`?

**Answer:**

- `ss` is faster and is the modern replacement for `netstat`.
- `netstat` provides similar network information but is considered legacy on most Linux distributions.

---

### 3. What does the `dig` command do?

**Answer:**

The `dig` command queries DNS servers and displays DNS records for a domain.

---

### 4. What is the purpose of `nslookup`?

**Answer:**

It retrieves DNS information and verifies domain name resolution.

---

### 5. Why is `traceroute` useful?

**Answer:**

It identifies each network hop between the source and destination, helping troubleshoot routing issues.

---

### 6. What information does the `arp` command display?

**Answer:**

It displays the ARP cache, showing IP addresses mapped to MAC addresses.

---

### 7. What is `tcpdump` used for?

**Answer:**

`tcpdump` captures and analyzes network packets for troubleshooting and forensic investigations.

---

# Summary

Network troubleshooting commands are essential for diagnosing connectivity problems, monitoring active connections, analyzing DNS resolution, inspecting network devices, and capturing traffic. These commands are widely used in SOC operations, incident response, malware analysis, and network security investigations.
