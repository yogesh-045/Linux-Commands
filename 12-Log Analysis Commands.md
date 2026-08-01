# 📋 Day 12 - Log Analysis Commands

Log analysis commands are used to search, filter, monitor, and analyze log files. These commands are essential for SOC Analysts during incident investigation, threat hunting, and system monitoring.

---

# Commands Summary

| Command | Syntax | Description |
|---------|--------|-------------|
| `tail -f` | `tail -f filename` | Displays the last lines of a file and continuously monitors new log entries in real time. |
| `grep` | `grep "pattern" filename` | Searches for a specific pattern or text within a file. |
| `awk` | `awk '{print $1}' filename` | Extracts and processes specific columns from text files. |
| `sed` | `sed 's/old/new/' filename` | Searches, replaces, and edits text in a file or stream. |
| `cut` | `cut -d':' -f1 filename` | Extracts specific fields or columns from a file. |
| `sort` | `sort filename` | Sorts lines alphabetically or numerically. |
| `uniq` | `uniq filename` | Removes or displays duplicate consecutive lines. |
| `wc` | `wc filename` | Counts lines, words, and characters in a file. |
| `tee` | `command \| tee output.txt` | Displays command output and saves it to a file simultaneously. |
| `journalctl` | `journalctl` | Displays logs collected by the systemd journal. |

---

# 1. tail -f

## Description

Displays the last lines of a file and continuously monitors new log entries in real time.

### Syntax

```bash
tail -f filename
```

### Example

```bash
tail -f /var/log/auth.log
```

### SOC Analyst Use Case

Monitor authentication logs in real time to detect failed or successful login attempts.

---

# 2. grep

## Description

Searches for a specific pattern or text within a file.

### Syntax

```bash
grep "pattern" filename
```

### Example

```bash
grep "Failed password" /var/log/auth.log
```

### SOC Analyst Use Case

Identify failed SSH login attempts or search for specific events in log files.

---

# 3. awk

## Description

Processes text and extracts specific columns or fields from log files.

### Syntax

```bash
awk '{print $1}' filename
```

### Example

```bash
awk '{print $1}' access.log
```

### SOC Analyst Use Case

Extract IP addresses, usernames, or timestamps from logs.

---

# 4. sed

## Description

Searches, replaces, and edits text within files or streams.

### Syntax

```bash
sed 's/old/new/' filename
```

### Example

```bash
sed 's/error/ERROR/g' log.txt
```

### SOC Analyst Use Case

Replace sensitive information or standardize log entries.

---

# 5. cut

## Description

Extracts selected fields from each line of a file.

### Syntax

```bash
cut -d':' -f1 filename
```

### Example

```bash
cut -d':' -f1 /etc/passwd
```

### SOC Analyst Use Case

Extract usernames or specific log fields for analysis.

---

# 6. sort

## Description

Sorts lines alphabetically or numerically.

### Syntax

```bash
sort filename
```

### Example

```bash
sort users.txt
```

### SOC Analyst Use Case

Sort IP addresses or usernames before further analysis.

---

# 7. uniq

## Description

Removes duplicate consecutive lines.

### Syntax

```bash
uniq filename
```

### Example

```bash
sort users.txt | uniq
```

### SOC Analyst Use Case

Identify unique IP addresses or user accounts.

---

# 8. wc

## Description

Counts lines, words, and characters in a file.

### Syntax

```bash
wc filename
```

### Example

```bash
wc auth.log
```

### SOC Analyst Use Case

Count the number of log entries or events.

---

# 9. tee

## Description

Displays command output on the terminal while simultaneously saving it to a file.

### Syntax

```bash
command | tee output.txt
```

### Example

```bash
grep "Failed" auth.log | tee failed_logins.txt
```

### SOC Analyst Use Case

Save investigation results while viewing them in real time.

---

# 10. journalctl

## Description

Displays logs managed by the systemd journal.

### Syntax

```bash
journalctl
```

### Example

```bash
journalctl -n 20
```

Monitor logs in real time:

```bash
journalctl -f
```

### SOC Analyst Use Case

Analyze system events, service failures, and authentication logs.

---

# Common SOC Analyst Commands

```bash
grep "Failed password" /var/log/auth.log

grep "Accepted password" /var/log/auth.log

grep "Failed password" /var/log/auth.log | wc -l

grep "Failed password" /var/log/auth.log | awk '{print $11}' | sort | uniq

tail -f /var/log/auth.log

journalctl -n 20

journalctl -f
```

---

# Interview Questions

### 1. What is the difference between `tail` and `tail -f`?

**Answer:**

- `tail` displays the last few lines of a file once.
- `tail -f` continuously monitors the file and displays new log entries in real time.

---

### 2. What is the purpose of the `grep` command?

**Answer:**

The `grep` command searches for a specific pattern or text within a file.

---

### 3. Why is `awk` commonly used in log analysis?

**Answer:**

It extracts and processes specific columns or fields from structured log files.

---

### 4. What does the `cut` command do?

**Answer:**

It extracts selected fields or columns from each line of a file.

---

### 5. Why do we use `sort` before `uniq`?

**Answer:**

Because `uniq` removes only consecutive duplicate lines. Sorting groups identical lines together.

---

### 6. What does `wc -l` display?

**Answer:**

It displays the total number of lines in a file.

---

### 7. What is the purpose of the `tee` command?

**Answer:**

It displays command output on the terminal and simultaneously saves it to a file.

---

# Summary

Log analysis commands help security analysts search, monitor, filter, and process log files efficiently. These commands are widely used in SOC environments for incident investigation, threat hunting, and troubleshooting Linux systems.
