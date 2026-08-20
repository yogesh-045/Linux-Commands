# 🐚 Day 21 - Bash Functions, Arguments & Input Validation

Bash functions allow us to create reusable blocks of code.

Command-line arguments allow users to pass information directly to a script.

Input validation helps ensure that the script receives valid and expected input.

These concepts are useful for creating reusable cybersecurity and SOC automation scripts.

---

# Concepts Summary

| Concept | Syntax | Description |
|---------|--------|-------------|
| Function | `name() { commands; }` | Creates a reusable block of commands. |
| Function Call | `name` | Executes a function. |
| `$1` | `$1` | First command-line argument. |
| `$2` | `$2` | Second command-line argument. |
| `$#` | `$#` | Number of command-line arguments. |
| `$@` | `$@` | All command-line arguments. |
| `$0` | `$0` | Name/path used to execute the script. |
| `read` | `read variable` | Takes input from the user. |
| `-z` | `[ -z "$var" ]` | Checks whether a string is empty. |
| `-n` | `[ -n "$var" ]` | Checks whether a string is not empty. |
| `return` | `return value` | Returns a status from a function. |

---

# 1. Bash Function

A function is a reusable block of commands.

### Syntax

```bash
function_name() {
    commands
}
```

## Example
```bash
#!/bin/bash

system_info() {
    hostname
    uptime
}

system_info
```
# 2. Function with Multiple Commands
```bash
#!/bin/bash

security_check() {
    echo "===== Security Check ====="


    echo "Current User:"
    whoami


    echo "Hostname:"
    hostname


    echo "System:"
    uname -a
}


security_check
```

# 3. Function Arguments

Arguments can be passed to functions.

## Example

```bash
#!/bin/bash

greet() {
    echo "Hello $1"
}

greet "SOC Analyst"
```
### Output:
```bash
Hello SOC Analyst
```
Inside a function:

```bash
$1 → First function argument
$2 → Second function argument
```

# 4. Command-Line Arguments

Command-line arguments are values provided when executing a script.

## Script

```bash
#!/bin/bash

echo "Script: $0"
echo "First argument: $1"
echo "Second argument: $2"
```
Run:
```bash
./script.sh Linux SOC
```

### Output:
```bash
Script: ./script.sh
First argument: Linux
Second argument: SOC
```

# 5. $# — Number of Arguments

$# contains the number of command-line arguments passed to the script.

## Example
```bash
#!/bin/bash

echo "Number of arguments: $#"
```
Run:
```bash
./script.sh Linux SOC Analyst
```
### Output:
```text
Number of arguments: 3
```

# 6. $@ — All Arguments

$@ represents all command-line arguments.

## Example
```bash
#!/bin/bash

for argument in "$@"
do
    echo "Argument: $argument"
done
```
Run:
```bash
./script.sh Linux SOC Security
```

### Output:
```bash
Argument: Linux
Argument: SOC
Argument: Security
```

# 7. $0 — Script Name

$0 contains the name or path used to execute the script.

## Example
```bash
#!/bin/bash

echo "Running script: $0"
```
Run:
```bash
./script.sh
```

# 8. read — User Input

read accepts input from the user.

## Example
```bash
#!/bin/bash

read -p "Enter username: " username

echo "Username: $username"
```

# 9. Input Validation

Input validation checks whether the user provided valid input before the script continues.

## Example
```bash
#!/bin/bash

read -p "Enter username: " username

if [ -z "$username" ]; then
    echo "Username cannot be empty"
else
    echo "Username: $username"
fi
```

# 10. Validate Number of Arguments

A script can verify that the required number of arguments was provided.

## Example
```bash
#!/bin/bash

if [ "$#" -lt 1 ]; then
    echo "Usage: $0 <filename>"
    exit 1
fi

echo "File provided: $1"
```

Run incorrectly:
```bash
./script.sh
```
### Output:
```bash
Usage: ./script.sh <filename>
```
Run correctly:
```bash
./script.sh report.txt
```

# 11. Function Return Status

A function can return a status code.

## Example
```bash
#!/bin/bash

check_file() {


    if [ -f "$1" ]; then
        echo "File exists"
        return 0
    else
        echo "File does not exist"
        return 1
    fi
}


check_file "/etc/passwd"

echo "Function status: $?"
```
# 🛡️ SOC Analyst Example
File Investigation Script
```bash
#!/bin/bash

check_file() {


    if [ -z "$1" ]; then
        echo "Error: No file provided"
        return 1
    fi


    if [ -f "$1" ]; then
        echo "File found: $1"


        echo "Permissions:"
        ls -l "$1"


        echo "File Type:"
        file "$1"


    else
        echo "File not found: $1"
        return 1
    fi
}


if [ "$#" -ne 1 ]; then
    echo "Usage: $0 <filename>"
    exit 1
fi


check_file "$1"
```
Run:
```bash
./file_check.sh suspicious.sh
```
This script:

1. Checks whether an argument was provided.
2. Checks whether the file exists.
3. Displays its permissions.
4. Displays its file type.

# 🎤 Interview Questions
## 1. What is a Bash function?

Answer:

A Bash function is a reusable block of commands that can be called multiple times within a script.

## 2. What does $1 represent?

Answer:

$1 represents the first command-line argument passed to a script or function.

## 3. What does $# represent?

Answer:

$# represents the number of command-line arguments passed to the script.

## 4. What does $@ represent?

Answer:

$@ represents all command-line arguments individually.

## 5. What does $0 represent?

Answer:

$0 represents the name or path used to execute the script.

## 6. Why is input validation important?

Answer:

Input validation ensures that a script receives expected and valid input before performing an operation. This helps prevent errors and unexpected behavior.

## 7. What does return 0 mean?

Answer:

It normally indicates successful execution of a function.

## 8. What does exit 1 do?

Answer:

It terminates the script and returns a non-zero exit status, generally indicating an error or failure.

# Summary

Bash functions, command-line arguments, and input validation make scripts more reusable and reliable.

These concepts allow SOC Analysts to build scripts that accept investigation targets, validate input, perform security checks, and return meaningful results.
