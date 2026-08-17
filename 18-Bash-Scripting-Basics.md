# 🐚 Day 18 - Bash Scripting Basics

Bash scripting allows us to automate repetitive tasks and execute multiple Linux commands using a single script.

For a SOC Analyst, Bash scripting is useful for automating system checks, log analysis, IOC searches, process investigation, and incident-response tasks.

---

# Commands & Concepts Summary

| Command / Concept | Syntax | Description |
|-------------------|--------|-------------|
| Shebang | `#!/bin/bash` | Specifies Bash as the interpreter for the script. |
| Variable | `NAME="value"` | Stores data in a variable. |
| `echo` | `echo "$NAME"` | Displays text or variable values. |
| `read` | `read NAME` | Takes input from the user. |
| `if` | `if [ condition ]; then` | Executes commands when a condition is true. |
| `else` | `else` | Executes commands when the `if` condition is false. |
| `elif` | `elif [ condition ]; then` | Checks another condition if the previous condition is false. |
| `for` | `for item in list` | Repeats commands for each item in a list. |
| `while` | `while [ condition ]` | Repeats commands while a condition is true. |
| `case` | `case "$var" in` | Performs actions based on different possible values. |
| Function | `function_name() { }` | Creates reusable blocks of commands. |
| `$?` | `echo $?` | Displays the exit status of the previous command. |
| `$0` | `echo $0` | Displays the name of the script. |
| `$1` | `echo $1` | Displays the first command-line argument. |
| `$2` | `echo $2` | Displays the second command-line argument. |

---

# 1. Shebang

## Description

The shebang tells Linux which interpreter should be used to execute the script.

### Syntax

```bash
#!/bin/bash
```

### Example

```bash
#!/bin/bash

echo "Hello Linux"
```

---

# 2. Creating a Bash Script

Create a script:

```bash
nano script.sh
```

Add:

```bash
#!/bin/bash

echo "Hello SOC Analyst"
```

Make it executable:

```bash
chmod +x script.sh
```

Run it:

```bash
./script.sh
```

---

# 3. Variables

## Description

Variables store information that can be used later in a script.

### Syntax

```bash
VARIABLE="value"
```

### Example

```bash
name="Yogesh"

echo "$name"
```

Output:

```text
Yogesh
```

> Do not put spaces around `=` when assigning a variable.

Correct:

```bash
name="Yogesh"
```

Incorrect:

```bash
name = "Yogesh"
```

---

# 4. echo

## Description

Displays text or variable values.

### Example

```bash
name="Yogesh"

echo "Hello $name"
```

Output:

```text
Hello Yogesh
```

---

# 5. read

## Description

Takes input from the user and stores it in a variable.

### Example

```bash
#!/bin/bash

echo "Enter your name:"
read name

echo "Hello $name"
```

---

# 6. if

## Description

Executes commands when a specified condition is true.

### Syntax

```bash
if [ condition ]; then
    command
fi
```

### Example

```bash
#!/bin/bash

user="kali"

if [ "$user" = "kali" ]; then
    echo "Kali user detected"
fi
```

---

# 7. else

## Description

Executes commands when the `if` condition is false.

### Example

```bash
#!/bin/bash

user="admin"

if [ "$user" = "kali" ]; then
    echo "Kali user detected"
else
    echo "Different user detected"
fi
```

---

# 8. elif

## Description

Checks another condition when the previous condition is false.

### Example

```bash
#!/bin/bash

number=10

if [ "$number" -gt 10 ]; then
    echo "Greater than 10"
elif [ "$number" -eq 10 ]; then
    echo "Equal to 10"
else
    echo "Less than 10"
fi
```

---

# 9. for Loop

## Description

Repeats commands for each item in a list.

### Example

```bash
#!/bin/bash

for user in kali root admin
do
    echo "User: $user"
done
```

Output:

```text
User: kali
User: root
User: admin
```

### SOC Analyst Use Case

Run the same security check against multiple files, IP addresses, or usernames.

---

# 10. while Loop

## Description

Repeats commands while a condition remains true.

### Example

```bash
#!/bin/bash

count=1

while [ "$count" -le 5 ]
do
    echo "Count: $count"
    count=$((count + 1))
done
```

---

# 11. case

## Description

Performs different actions depending on the value of a variable.

### Example

```bash
#!/bin/bash

read -p "Enter option: " option

case "$option" in
    1)
        echo "System Information"
        ;;
    2)
        echo "Network Information"
        ;;
    3)
        echo "Process Information"
        ;;
    *)
        echo "Invalid option"
        ;;
esac
```

### SOC Analyst Use Case

Create menu-based investigation scripts.

---

# 12. Functions

## Description

Functions allow us to create reusable blocks of commands.

### Syntax

```bash
function_name() {
    commands
}
```

### Example

```bash
#!/bin/bash

system_info() {
    hostname
    uptime
    free -h
}

system_info
```

---

# 13. Exit Status `$?`

## Description

`$?` stores the exit status of the most recently executed command.

Usually:

```text
0 → Success
Non-zero → Error/Failure
```

### Example

```bash
ls /home/kali

echo $?
```

If the command succeeds:

```text
0
```

If the command fails, a non-zero value is returned.

### SOC Analyst Use Case

Check whether security scripts or investigation commands executed successfully.

---

# 14. `$0`

## Description

`$0` contains the name of the currently running script.

### Example

```bash
#!/bin/bash

echo "Script name: $0"
```

Run:

```bash
./script.sh
```

---

# 15. `$1` and `$2`

## Description

`$1`, `$2`, etc. represent command-line arguments passed to the script.

### Example

Create:

```bash
#!/bin/bash

echo "First argument: $1"
echo "Second argument: $2"
```

Run:

```bash
./script.sh Linux SOC
```

Output:

```text
First argument: Linux
Second argument: SOC
```

---

# 🛡️ SOC Analyst Example

A simple system information script:

```bash
#!/bin/bash

echo "===== SOC System Check ====="

echo "Hostname:"
hostname

echo "Current User:"
whoami

echo "System Information:"
uname -a

echo "IP Information:"
ip addr

echo "Running Processes:"
ps aux

echo "Memory Usage:"
free -h
```

Save as:

```bash
soc_check.sh
```

Make executable:

```bash
chmod +x soc_check.sh
```

Run:

```bash
./soc_check.sh
```

---

# 🔍 SOC Log Investigation Example

Search for failed SSH login attempts:

```bash
#!/bin/bash

echo "===== Failed SSH Login Attempts ====="

grep "Failed password" /var/log/auth.log
```

Count failed attempts:

```bash
#!/bin/bash

count=$(grep -c "Failed password" /var/log/auth.log)

echo "Failed login attempts: $count"
```

---

# 🎤 Interview Questions

### 1. What is Bash scripting?

**Answer:**

Bash scripting is the process of writing a sequence of Linux shell commands in a script to automate tasks.

---

### 2. What is a shebang?

**Answer:**

A shebang specifies which interpreter should execute the script.

Example:

```bash
#!/bin/bash
```

---

### 3. How do you make a Bash script executable?

**Answer:**

Use:

```bash
chmod +x script.sh
```

Then execute it with:

```bash
./script.sh
```

---

### 4. What is a variable in Bash?

**Answer:**

A variable stores a value that can be used later in a script.

Example:

```bash
name="Yogesh"
```

---

### 5. What does `$?` represent?

**Answer:**

`$?` contains the exit status of the previously executed command.

```text
0     → Success
Non-0 → Failure/Error
```

---

### 6. What are `$0`, `$1`, and `$2`?

**Answer:**

- `$0` → Script name
- `$1` → First argument
- `$2` → Second argument

---

### 7. What is the purpose of an `if` statement?

**Answer:**

It allows a script to execute commands based on whether a condition is true or false.

---

### 8. What is the difference between `for` and `while` loops?

**Answer:**

- `for` is commonly used to iterate through a known list or range.
- `while` continues running as long as its condition remains true.

---

### 9. Why is Bash scripting useful for SOC Analysts?

**Answer:**

Bash scripting can automate repetitive tasks such as log analysis, system information gathering, IOC searches, process checks, and incident-response activities.

---

# 🧪 Practice Lab

Create a script:

```bash
nano practice.sh
```

Add:

```bash
#!/bin/bash

echo "===== Linux Security Check ====="

echo "Hostname:"
hostname

echo "Current User:"
whoami

echo "System:"
uname -a

echo "Memory:"
free -h

echo "Network:"
ip addr

echo "Failed Login Attempts:"
grep -c "Failed password" /var/log/auth.log
```

Make it executable:

```bash
chmod +x practice.sh
```

Run:

```bash
./practice.sh
```

---

# 🎯 Quick Revision

| Concept | Remember |
|---------|----------|
| `#!/bin/bash` | Bash interpreter |
| Variable | Stores data |
| `echo` | Displays output |
| `read` | Takes user input |
| `if` | Condition |
| `else` | Alternative condition |
| `elif` | Additional condition |
| `for` | Loop through items |
| `while` | Loop while condition is true |
| `case` | Multiple choices |
| Function | Reusable commands |
| `$?` | Previous command's exit status |
| `$0` | Script name |
| `$1` | First argument |
| `$2` | Second argument |

---

# Summary

Bash scripting is an important Linux skill for cybersecurity professionals.

It allows SOC Analysts to automate repetitive investigation tasks, collect system information, analyze logs, search for indicators of compromise, and perform basic incident-response actions efficiently.

The goal is to move from **running individual Linux commands** to **combining commands into useful security automation scripts**.
