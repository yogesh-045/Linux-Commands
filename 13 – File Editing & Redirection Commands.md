# ✏️ Day 13 - File Editing & Redirection Commands

File editing and redirection commands are used to create, edit, and manage text files. They also allow users to redirect command output or input, making them essential for Linux administration, scripting, and SOC Analyst investigations.

---

# Commands Summary

| Command | Syntax | Description |
|---------|--------|-------------|
| `nano` | `nano filename` | Opens a file in the Nano text editor. |
| `vim` | `vim filename` | Opens a file in the Vim text editor. |
| `vi` | `vi filename` | Opens a file in the Vi text editor. |
| `echo` | `echo "text"` | Displays text or writes text to a file. |
| `printf` | `printf "text"` | Prints formatted text to the terminal or a file. |
| `>` | `command > file` | Redirects output to a file and overwrites existing content. |
| `>>` | `command >> file` | Appends output to the end of a file without overwriting. |
| `<` | `command < file` | Uses a file as the input for a command. |
| `cat >` | `cat > filename` | Creates a new file and writes content from the keyboard. |
| `cat >>` | `cat >> filename` | Appends content to an existing file. |

---

# 1. nano

## Description

A simple terminal-based text editor that is beginner-friendly.

### Syntax

```bash
nano filename
```

### Example

```bash
nano notes.txt
```

### Save

```text
Ctrl + O
```

### Exit

```text
Ctrl + X
```

### SOC Analyst Use Case

Edit IOC lists, notes, configuration files, and investigation reports directly from the terminal.

---

# 2. vim

## Description

A powerful and advanced terminal text editor used by Linux administrators and developers.

### Syntax

```bash
vim filename
```

### Example

```bash
vim notes.txt
```

### Common Commands

| Key | Function |
|------|----------|
| `i` | Enter Insert Mode |
| `Esc` | Exit Insert Mode |
| `:w` | Save File |
| `:q` | Quit |
| `:wq` | Save and Quit |
| `:q!` | Quit Without Saving |

### SOC Analyst Use Case

Edit configuration files and large log files on Linux servers.

---

# 3. vi

## Description

The original Unix text editor. Basic usage is similar to Vim.

### Syntax

```bash
vi filename
```

### Example

```bash
vi notes.txt
```

### SOC Analyst Use Case

Modify files on systems where Vim is not installed.

---

# 4. echo

## Description

Displays text on the terminal or writes text to a file.

### Syntax

```bash
echo "text"
```

### Example

```bash
echo "SOC Analyst"
```

Write to a file:

```bash
echo "Linux Commands" > notes.txt
```

Append to a file:

```bash
echo "Day 13 Completed" >> notes.txt
```

### SOC Analyst Use Case

Create quick notes, save investigation results, or generate simple reports.

---

# 5. printf

## Description

Prints formatted text with better formatting control than `echo`.

### Syntax

```bash
printf "text"
```

### Example

```bash
printf "Name: Yogesh\nRole: SOC Analyst\n"
```

Write to a file:

```bash
printf "Linux Commands\n" > notes.txt
```

### SOC Analyst Use Case

Generate structured reports or formatted output.

---

# 6. > (Output Redirection)

## Description

Redirects command output to a file and overwrites existing content.

### Syntax

```bash
command > filename
```

### Example

```bash
ls > files.txt
```

### SOC Analyst Use Case

Save command output for documentation or investigation.

---

# 7. >> (Append Redirection)

## Description

Appends command output to the end of an existing file.

### Syntax

```bash
command >> filename
```

### Example

```bash
date >> logs.txt
```

### SOC Analyst Use Case

Maintain investigation logs without losing previous entries.

---

# 8. < (Input Redirection)

## Description

Uses a file as input for a command.

### Syntax

```bash
command < filename
```

### Example

```bash
sort < names.txt
```

### SOC Analyst Use Case

Process input data from files instead of typing manually.

---

# 9. cat >

## Description

Creates a new file and allows users to enter content directly from the keyboard.

### Syntax

```bash
cat > filename
```

### Example

```bash
cat > notes.txt
```

Type your content and press:

```text
Ctrl + D
```

### SOC Analyst Use Case

Quickly create investigation notes or IOC files.

---

# 10. cat >>

## Description

Appends new content to an existing file.

### Syntax

```bash
cat >> filename
```

### Example

```bash
cat >> notes.txt
```

Press:

```text
Ctrl + D
```

to save.

### SOC Analyst Use Case

Append new findings to an investigation report.

---

# Common SOC Analyst Commands

```bash
ps aux > processes.txt

grep "Failed password" /var/log/auth.log > failed_logins.txt

echo "Suspicious IP Found" >> investigation.txt

nano ioc_list.txt

cat investigation.txt
```

---

# Interview Questions

### 1. What is the difference between `>` and `>>`?

**Answer:**

- `>` redirects output and overwrites the existing file.
- `>>` redirects output and appends it to the existing file.

---

### 2. What is Nano?

**Answer:**

Nano is a beginner-friendly terminal-based text editor used to create and edit text files.

---

### 3. What is the difference between Vim and Nano?

**Answer:**

- Nano is simple and easy to use.
- Vim is more powerful and feature-rich but has a steeper learning curve.

---

### 4. What does the `echo` command do?

**Answer:**

The `echo` command displays text on the terminal or writes text to a file.

---

### 5. What is the purpose of the `printf` command?

**Answer:**

The `printf` command prints formatted text and provides more formatting control than `echo`.

---

### 6. What does `cat > file` do?

**Answer:**

It creates a new file (or overwrites an existing file) and allows the user to enter content from the keyboard.

---

### 7. How do you append text to an existing file?

**Answer:**

Using:

```bash
echo "text" >> file.txt
```

or

```bash
cat >> file.txt
```

---

# Summary

File editing and redirection commands are used to create, edit, format, and save files. They also allow command output to be redirected into files, making them essential for Linux administration, automation, scripting, and SOC Analyst investigations.
