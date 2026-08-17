# 🐚 Day 19 - Bash Conditions

Bash conditions allow scripts to make decisions based on files, directories, strings, numbers, and command results.

Conditions are very useful in cybersecurity automation because a script can check whether a log file exists, whether a file is readable, whether a process is running, or whether a value meets a specific condition.

---

# Conditions Summary

| Operator | Description |
|----------|-------------|
| `-f` | Checks whether a regular file exists. |
| `-d` | Checks whether a directory exists. |
| `-e` | Checks whether a file or directory exists. |
| `-r` | Checks whether a file is readable. |
| `-w` | Checks whether a file is writable. |
| `-x` | Checks whether a file is executable. |
| `-z` | Checks whether a string is empty. |
| `-n` | Checks whether a string is not empty. |
| `-eq` | Numbers are equal. |
| `-ne` | Numbers are not equal. |
| `-gt` | Greater than. |
| `-lt` | Less than. |
| `-ge` | Greater than or equal to. |
| `-le` | Less than or equal to. |

---

# 1. `-f` — Check File

## Description

Checks whether a regular file exists.

### Example

```bash
if [ -f "/etc/passwd" ]; then
    echo "File exists"
else
    echo "File not found"
fi
```

### SOC Analyst Use Case

Check whether an important log or configuration file exists.

---

# 2. `-d` — Check Directory

## Description

Checks whether a directory exists.

### Example

```bash
if [ -d "/var/log" ]; then
    echo "Log directory exists"
else
    echo "Directory not found"
fi
```

---

# 3. `-e` — Check Existence

## Description

Checks whether a file or directory exists.

### Example

```bash
if [ -e "/etc/passwd" ]; then
    echo "Path exists"
fi
```

### Difference

```text
-f → Regular file
-d → Directory
-e → File OR directory
```

---

# 4. `-r` — Check Read Permission

## Description

Checks whether a file is readable by the current user.

### Example

```bash
if [ -r "report.txt" ]; then
    echo "File is readable"
else
    echo "File is not readable"
fi
```

---

# 5. `-w` — Check Write Permission

## Description

Checks whether a file is writable by the current user.

### Example

```bash
if [ -w "report.txt" ]; then
    echo "File is writable"
else
    echo "File is not writable"
fi
```

---

# 6. `-x` — Check Execute Permission

## Description

Checks whether a file is executable by the current user.

### Example

```bash
if [ -x "script.sh" ]; then
    echo "File is executable"
else
    echo "File is not executable"
fi
```

### SOC Analyst Use Case

Check suspicious scripts or binaries for executable permissions.

---

# 7. `-z` — Check Empty String

## Description

Checks whether a string has zero length.

### Example

```bash
name=""

if [ -z "$name" ]; then
    echo "String is empty"
fi
```

---

# 8. `-n` — Check Non-Empty String

## Description

Checks whether a string is not empty.

### Example

```bash
name="kali"

if [ -n "$name" ]; then
    echo "String is not empty"
fi
```

---

# 9. `-eq` — Equal

## Description

Checks whether two numbers are equal.

### Example

```bash
count=10

if [ "$count" -eq 10 ]; then
    echo "Count is 10"
fi
```

---

# 10. `-ne` — Not Equal

## Description

Checks whether two numbers are not equal.

### Example

```bash
count=5

if [ "$count" -ne 10 ]; then
    echo "Count is not 10"
fi
```

---

# 11. `-gt` — Greater Than

## Description

Checks whether one number is greater than another.

### Example

```bash
count=10

if [ "$count" -gt 5 ]; then
    echo "Count is greater than 5"
fi
```

---

# 12. `-lt` — Less Than

## Description

Checks whether one number is less than another.

### Example

```bash
count=3

if [ "$count" -lt 5 ]; then
    echo "Count is less than 5"
fi
```

---

# 13. `-ge` — Greater Than or Equal

## Description

Checks whether a number is greater than or equal to another number.

### Example

```bash
count=10

if [ "$count" -ge 10 ]; then
    echo "Count is greater than or equal to 10"
fi
```

---

# 14. `-le` — Less Than or Equal

## Description

Checks whether a number is less than or equal to another number.

### Example

```bash
count=5

if [ "$count" -le 5 ]; then
    echo "Count is less than or equal to 5"
fi
```

---

# 🛡️ SOC Analyst Example

## Check Authentication Log

```bash
#!/bin/bash

LOG="/var/log/auth.log"

if [ -f "$LOG" ]; then
    echo "Authentication log found"
else
    echo "Authentication log not found"
fi
```

---

# 🛡️ Check Log Permissions

```bash
#!/bin/bash

LOG="/var/log/auth.log"

if [ -r "$LOG" ]; then
    echo "Log is readable"
else
    echo "Log is not readable"
fi
```

---

# 🛡️ Check Suspicious Script

```bash
#!/bin/bash

FILE="suspicious.sh"

if [ -f "$FILE" ]; then

    echo "File found"

    if [ -x "$FILE" ]; then
        echo "WARNING: File is executable"
    else
        echo "File is not executable"
    fi

else
    echo "File not found"
fi
```

---

# 🎤 Interview Questions

### 1. What is the purpose of `-f` in Bash?

**Answer:**

`-f` checks whether a path exists and is a regular file.

```bash
if [ -f "file.txt" ]; then
    echo "File exists"
fi
```

---

### 2. What is the difference between `-f`, `-d`, and `-e`?

**Answer:**

```text
-f → Checks for a regular file
-d → Checks for a directory
-e → Checks whether the path exists
```

---

### 3. What does `-r` check?

**Answer:**

It checks whether the current user has read permission for the file.

---

### 4. What does `-x` check?

**Answer:**

It checks whether the file is executable by the current user.

---

### 5. What is the difference between `-eq` and `=`?

**Answer:**

`-eq` is used for numeric comparison, while `=` is commonly used for string comparison.

Example:

```bash
[ "$count" -eq 10 ]
```

Numeric comparison.

```bash
[ "$user" = "kali" ]
```

String comparison.

---

### 6. What does `$?` represent?

**Answer:**

`$?` contains the exit status of the previously executed command.

```text
0     → Success
Non-0 → Failure/Error
```

---

### 7. Why are Bash conditions useful for SOC Analysts?

**Answer:**

They allow analysts to automate security checks based on files, permissions, logs, processes, and command results.

---

# 🧪 Practice Lab

Create a script:

```bash
nano conditions.sh
```

Add:

```bash
#!/bin/bash

LOG="/var/log/auth.log"

echo "===== File Check ====="

if [ -f "$LOG" ]; then
    echo "Authentication log exists"
else
    echo "Authentication log does not exist"
fi

echo "===== Permission Check ====="

if [ -r "$LOG" ]; then
    echo "Authentication log is readable"
else
    echo "Authentication log is not readable"
fi
```

Make it executable:

```bash
chmod +x conditions.sh
```

Run:

```bash
./conditions.sh
```

---

# 🎯 Quick Revision

| Operator | Remember |
|----------|----------|
| `-f` | File exists |
| `-d` | Directory exists |
| `-e` | Path exists |
| `-r` | Readable |
| `-w` | Writable |
| `-x` | Executable |
| `-z` | String is empty |
| `-n` | String is not empty |
| `-eq` | Equal |
| `-ne` | Not equal |
| `-gt` | Greater than |
| `-lt` | Less than |
| `-ge` | Greater/equal |
| `-le` | Less/equal |

---

# Summary

Bash conditions allow scripts to make decisions automatically.

They can be used to check:

- Files
- Directories
- Permissions
- Strings
- Numbers
- Security logs
- Suspicious scripts
- Investigation conditions

Understanding Bash conditions is an important step toward creating practical cybersecurity automation scripts.
