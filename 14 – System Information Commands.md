# 💻 Day 14 - System Information Commands

System Information commands are used to gather information about the Linux operating system, hardware, CPU, memory, hostname, kernel, date, and system uptime. These commands are essential for Linux administration, troubleshooting, and SOC Analyst investigations.

---

# Commands Summary

| Command | Syntax | Description |
|---------|--------|-------------|
| `uname` | `uname` | Displays the operating system name. |
| `uname -a` | `uname -a` | Displays complete system information including kernel version and architecture. |
| `hostname` | `hostname` | Displays the system hostname. |
| `hostnamectl` | `hostnamectl` | Displays detailed hostname and operating system information. |
| `uptime` | `uptime` | Displays system uptime, logged-in users, and load average. |
| `free` | `free` | Displays memory (RAM) and swap usage. |
| `free -h` | `free -h` | Displays memory usage in a human-readable format. |
| `lscpu` | `lscpu` | Displays CPU architecture and processor information. |
| `lsusb` | `lsusb` | Lists all connected USB devices. |
| `lspci` | `lspci` | Lists all PCI hardware devices. |
| `date` | `date` | Displays the current system date and time. |
| `cal` | `cal` | Displays the current month's calendar. |
| `timedatectl` | `timedatectl` | Displays and manages the system date, time, and timezone. |

---

# 1. uname

## Description

Displays the operating system name.

### Syntax

```bash
uname
```

### Example

```bash
uname
```

### Output

```text
Linux
```

### SOC Analyst Use Case

Identify the operating system before performing incident investigation or vulnerability assessment.

---

# 2. uname -a

## Description

Displays complete system information.

### Syntax

```bash
uname -a
```

### Example

```bash
uname -a
```

### Example Output

```text
Linux kali 6.12.13-amd64 #1 SMP x86_64 GNU/Linux
```

### SOC Analyst Use Case

Identify the Linux kernel version, hostname, and architecture while investigating compromised systems.

---

# 3. hostname

## Description

Displays the hostname (computer name).

### Syntax

```bash
hostname
```

### Example

```bash
hostname
```

### Output

```text
kali
```

### SOC Analyst Use Case

Identify which Linux machine generated a particular log or alert.

---

# 4. hostnamectl

## Description

Displays detailed hostname, operating system, kernel version, architecture, and hardware information.

### Syntax

```bash
hostnamectl
```

### Example

```bash
hostnamectl
```

### SOC Analyst Use Case

Collect detailed system information during incident response.

---

# 5. uptime

## Description

Displays the current time, system uptime, logged-in users, and load average.

### Syntax

```bash
uptime
```

### Example

```bash
uptime
```

### Example Output

```text
14:20:10 up 3 hours, 1 user, load average: 0.12, 0.18, 0.20
```

### SOC Analyst Use Case

Verify whether the server has recently rebooted and check overall system load.

---

# 6. free

## Description

Displays RAM and swap memory usage.

### Syntax

```bash
free
```

### Example

```bash
free
```

### SOC Analyst Use Case

Check memory usage during malware analysis or incident investigation.

---

# 7. free -h

## Description

Displays memory usage in a human-readable format.

### Syntax

```bash
free -h
```

### Example

```bash
free -h
```

### SOC Analyst Use Case

Quickly verify available memory before running forensic or security tools.

---

# 8. lscpu

## Description

Displays detailed CPU information.

### Syntax

```bash
lscpu
```

### Example

```bash
lscpu
```

### Information Displayed

- CPU Architecture
- CPU Model
- Number of CPUs
- CPU Cores
- Threads
- Virtualization Support

### SOC Analyst Use Case

Verify processor architecture before installing security software or forensic tools.

---

# 9. lsusb

## Description

Lists all connected USB devices.

### Syntax

```bash
lsusb
```

### Example

```bash
lsusb
```

### SOC Analyst Use Case

Identify connected USB storage devices during forensic investigations.

---

# 10. lspci

## Description

Lists all PCI hardware devices.

### Syntax

```bash
lspci
```

### Example

```bash
lspci
```

### Information Displayed

- Graphics Card
- Network Adapter
- Audio Controller
- SATA Controller

### SOC Analyst Use Case

Identify installed network cards or hardware during investigations.

---

# 11. date

## Description

Displays the current system date and time.

### Syntax

```bash
date
```

### Example

```bash
date
```

### SOC Analyst Use Case

Verify timestamps while analyzing security logs.

---

# 12. cal

## Description

Displays the current month's calendar.

### Syntax

```bash
cal
```

### Example

```bash
cal
```

Display a specific year:

```bash
cal 2026
```

### SOC Analyst Use Case

Useful for verifying dates during timeline analysis.

---

# 13. timedatectl

## Description

Displays and manages the system date, time, timezone, and NTP synchronization.

### Syntax

```bash
timedatectl
```

### Example

```bash
timedatectl
```

### SOC Analyst Use Case

Verify system time synchronization to ensure accurate log timestamps.

---

# Common SOC Analyst Commands

```bash
uname -a

hostname

hostnamectl

uptime

free -h

lscpu

lsusb

lspci

date

timedatectl
```

---

# Interview Questions

### 1. What does the `uname` command do?

**Answer:**

The `uname` command displays basic information about the operating system.

---

### 2. What is the difference between `uname` and `uname -a`?

**Answer:**

- `uname` displays only the operating system name.
- `uname -a` displays detailed information including the kernel version, hostname, and system architecture.

---

### 3. What information does the `free -h` command provide?

**Answer:**

It displays RAM and swap memory usage in a human-readable format (KB, MB, GB).

---

### 4. What is the purpose of the `hostname` command?

**Answer:**

It displays the current system's hostname (computer name).

---

### 5. Why is the `timedatectl` command important?

**Answer:**

It verifies the system date, time, timezone, and NTP synchronization, ensuring log timestamps are accurate.

---

### 6. What does the `uptime` command display?

**Answer:**

It displays the current time, system uptime, logged-in users, and load average.

---

### 7. What is the difference between `lsusb` and `lspci`?

**Answer:**

- `lsusb` lists USB devices connected to the system.
- `lspci` lists PCI hardware devices such as graphics cards, network adapters, and storage controllers.

---

# Summary

System Information commands help Linux administrators and SOC Analysts identify operating system details, hardware configuration, CPU information, memory usage, hostname, kernel version, system uptime, and time settings. These commands are commonly used during troubleshooting, incident response, forensic investigations, and security assessments.
