# 🐧 Day 16 - Environment Variables & Shell Commands

Environment variables and shell commands are used to manage the shell environment, inspect command locations, create command shortcuts, and review previously executed commands.

These commands are useful for Linux administration, troubleshooting, scripting, and SOC Analyst investigations.

---

# Commands Summary

| Command | Syntax | Description |
|---------|--------|-------------|
| `env` | `env` | Displays environment variables. |
| `printenv` | `printenv [VARIABLE]` | Displays environment variables or a specific variable. |
| `export` | `export VAR=value` | Creates or modifies an environment variable. |
| `alias` | `alias name='command'` | Creates a shortcut for a command. |
| `unalias` | `unalias name` | Removes an existing alias. |
| `history` | `history` | Displays previously executed shell commands. |
| `which` | `which command` | Shows the executable path selected through `PATH`. |
| `whereis` | `whereis command` | Locates the binary, source, and manual page of a command. |
| `type` | `type command` | Shows how the shell interprets a command. |

---

# 1. env

## Description

Displays the current environment variables.

### Syntax

```bash
env
```

### Example

```bash
env
```

### Example Output

```text
HOME=/home/kali
USER=kali
SHELL=/usr/bin/zsh
PATH=/usr/local/bin:/usr/bin:/bin
```

### SOC Analyst Use Case

Check environment variables during system investigation or troubleshooting.

---

# 2. printenv

## Description

Displays environment variables or the value of a specific variable.

### Syntax

```bash
printenv
```

### Example

```bash
printenv HOME
```

### Output

```text
/home/kali
```

### SOC Analyst Use Case

Check important environment variables such as `HOME`, `USER`, `SHELL`, and `PATH`.

---

# 3. export

## Description

Creates or modifies an environment variable and makes it available to processes started from the current shell.

### Syntax

```bash
export VARIABLE=value
```

### Example

```bash
export NAME="SOC Analyst"
```

Check the variable:

```bash
echo $NAME
```

### Output

```text
SOC Analyst
```

### Note

The variable normally exists only for the current shell session unless it is added to a shell startup/configuration file.

---

# 4. alias

## Description

Creates a shortcut for a command.

### Syntax

```bash
alias name='command'
```

### Example

```bash
alias ll='ls -la'
```

Now:

```bash
ll
```

is equivalent to:

```bash
ls -la
```

View existing aliases:

```bash
alias
```

### SOC Analyst Use Case

Create shortcuts for frequently used investigation commands.

---

# 5. unalias

## Description

Removes an existing alias.

### Syntax

```bash
unalias name
```

### Example

```bash
unalias ll
```

The `ll` alias is now removed.

---

# 6. history

## Description

Displays previously executed commands in the shell.

### Syntax

```bash
history
```

### Example

```bash
history
```

Search command history:

```bash
history | grep ssh
```

Search for sudo commands:

```bash
history | grep sudo
```

### SOC Analyst Use Case

Command history can provide useful context about commands previously executed by a user during an investigation.

> **Note:** Shell history is not a complete audit log. Users may clear or modify it, and some commands may not be recorded.

---

# 7. which

## Description

Shows the path of an executable command found through the current `PATH`.

### Syntax

```bash
which command
```

### Example

```bash
which python
```

Possible output:

```text
/usr/bin/python
```

Another example:

```bash
which ls
```

### SOC Analyst Use Case

Verify which executable will be used when a command is executed.

---

# 8. whereis

## Description

Locates files associated with a command, such as its binary, source files, and manual pages.

### Syntax

```bash
whereis command
```

### Example

```bash
whereis python
```

Possible output:

```text
python: /usr/bin/python /usr/share/man/man1/python.1.gz
```

### SOC Analyst Use Case

Locate binaries and documentation associated with commands during system investigation.

---

# 9. type

## Description

Shows how the shell interprets a command.

A command may be an alias, shell builtin, function, or executable.

### Syntax

```bash
type command
```

### Example

```bash
type ls
```

Possible output:

```text
ls is aliased to `ls --color=auto`
```

Another example:

```bash
type cd
```

Possible output:

```text
cd is a shell builtin
```

### SOC Analyst Use Case

Determine whether a command is an alias, builtin, function, or external executable.

---

# Common SOC Analyst Commands

```bash
env

printenv HOME

echo $USER

echo $PATH

export TEST="Linux"

echo $TEST

alias ll='ls -la'

type ll

which ls

whereis ls

history

history | grep sudo
```

---

# Interview Questions

### 1. What is an environment variable?

**Answer:**

An environment variable is a key-value pair that stores information used by the shell and processes, such as `PATH`, `HOME`, `USER`, and `SHELL`.

---

### 2. What is the difference between `env` and `printenv`?

**Answer:**

Both commands can display environment variables. `printenv` can also display the value of a specific variable directly.

Example:

```bash
printenv HOME
```

---

### 3. What does the `export` command do?

**Answer:**

`export` creates or modifies an environment variable and makes it available to processes started from the current shell.

---

### 4. What is an alias?

**Answer:**

An alias is a shortcut that maps a custom name to a command.

Example:

```bash
alias ll='ls -la'
```

---

### 5. What is the difference between `which` and `whereis`?

**Answer:**

- `which` shows the executable selected through the current `PATH`.
- `whereis` searches for related files such as binaries, source files, and manual pages.

---

### 6. What does the `history` command do?

**Answer:**

It displays commands previously entered in the shell history.

---

### 7. Is Linux shell history a complete audit log?

**Answer:**

No. Shell history is not a complete audit mechanism because users can clear or modify their history, and some commands may not be recorded.

---

### 8. What does the `type` command do?

**Answer:**

It shows how the shell interprets a command, such as an alias, shell builtin, function, or executable.



# Summary

Environment variables and shell commands help users understand and manage the Linux shell environment. They are also useful for troubleshooting, scripting, command verification, and SOC investigations.

Understanding commands such as `history`, `which`, `whereis`, and `type` is especially useful when investigating suspicious activity on Linux systems.
