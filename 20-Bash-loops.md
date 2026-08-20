# 🐚 Day 20 - Bash Loops & Automation

Bash loops are used to execute a set of commands repeatedly.

Loops are useful for automating repetitive tasks such as checking multiple files, IP addresses, users, processes, and log entries.

For SOC Analysts, loops can help automate repetitive investigation and system-monitoring tasks.

---

# Loops Summary

| Loop / Command | Syntax | Description |
|----------------|--------|-------------|
| `for` | `for item in list` | Executes commands for each item in a list. |
| `while` | `while [ condition ]` | Repeats commands while a condition is true. |
| `until` | `until [ condition ]` | Repeats commands until a condition becomes true. |
| `break` | `break` | Stops the current loop. |
| `continue` | `continue` | Skips the current iteration and continues the loop. |
| `$(( ))` | `$((expression))` | Performs arithmetic operations. |

---

# 1. for Loop

## Description

The `for` loop executes commands for each item in a list.

### Syntax

```bash
for variable in list
do
    commands
done
```
## Example
```bash
#!/bin/bash

for user in kali root admin
do
    echo "User: $user"
done
```
### Output
```bash
User: kali
User: root
User: admin
```
# 2. for Loop with Numbers

A loop can be used to process a range of numbers.

## Example
```bash
#!/bin/bash

for number in {1..5}
do
    echo "Number: $number"
done
```
### Output
```bash
Number: 1
Number: 2
Number: 3
Number: 4
Number: 5
```

# 3. Loop Through Files

A for loop can process multiple files.

## Example
```bash
#!/bin/bash

for file in *.txt
do
    echo "Checking: $file"
done
```
### SOC Analyst Use Case

Process multiple log or text files automatically.

# 4. while Loop

The while loop continues executing while a condition is true.

### Syntax
```bash
while [ condition ]
do
    commands
done
```
## Example
```bash
#!/bin/bash

count=1

while [ "$count" -le 5 ]
do
    echo "Count: $count"
    count=$((count + 1))
done
```

# 5. until Loop

The until loop continues executing until the specified condition becomes true.

## Example
```bash
#!/bin/bash

count=1

until [ "$count" -gt 5 ]
do
    echo "Count: $count"
    count=$((count + 1))
done
```
# 6. break

break immediately stops the current loop.

## Example
```bash
#!/bin/bash

for number in {1..10}
do
    if [ "$number" -eq 5 ]; then
        break
    fi

    echo "$number"
done
```
### Output
```bash
1
2
3
4
```
# 7. continue

continue skips the current iteration and moves to the next iteration.

## Example
```bash
#!/bin/bash

for number in {1..5}
do
    if [ "$number" -eq 3 ]; then
        continue
    fi

    echo "$number"
done
```

### Output
```bash
1
2
4
5
```

# 8. Arithmetic with $(( ))

$(( )) is used to perform arithmetic calculations in Bash.

## Example
```bash
count=10

count=$((count + 1))

echo "$count"
```
### Output:
```bash
11
```
### Other Operations
```bash
a=$((10 + 5))
b=$((10 - 5))
c=$((10 * 5))
d=$((10 / 5))
```

# 🛡️ SOC Analyst Examples
## 1. Check Multiple IP Addresses
```bash
#!/bin/bash

for ip in 192.168.1.1 192.168.1.10 192.168.1.20
do
    echo "Checking $ip"
    ping -c 1 "$ip" > /dev/null

    if [ "$?" -eq 0 ]; then
        echo "$ip is reachable"
    else
        echo "$ip is not reachable"
    fi
done
```
## 2. Check Multiple Files
```bash
#!/bin/bash

for file in *.log
do
    if [ -f "$file" ]; then
        echo "Found log file: $file"
    fi
done
```
## 3. Search for Failed Login Attempts
```bash
#!/bin/bash

for file in /var/log/*.log
do
    if [ -f "$file" ]; then
        echo "Checking: $file"
        grep -i "failed" "$file"
    fi
done
```

> Log locations and filenames can differ between Linux distributions.

# 🎤 Interview Questions
## 1. What is a loop in Bash?

A loop repeatedly executes a block of commands while iterating through a list or while a specified condition is satisfied.

## 2. What is the difference between for and while?

for is commonly used to iterate through a known list or range.
while continues executing as long as its condition is true.

## 3. What does break do?

break immediately terminates the current loop.

## 4. What does continue do?

continue skips the current iteration and proceeds to the next iteration of the loop.

## 5. What is an until loop?

An until loop repeatedly executes commands until its condition becomes true.

## 6. How do you perform arithmetic in Bash?

Bash commonly uses arithmetic expansion:
```bash
result=$((10 + 5))
```
## 7. Why are loops useful for SOC Analysts?

Loops can automate repetitive security tasks such as checking multiple files, IP addresses, logs, users, or system resources.

# Summary

Bash loops allow repetitive tasks to be automated efficiently.

They can be combined with conditions, commands, variables, and functions to create practical cybersecurity automation scripts.

For SOC operations, loops can be used to automate repetitive tasks such as:

- Checking multiple files
- Searching multiple logs
- Testing multiple IP addresses
- Checking multiple users
- Performing repeated system checks
- Automating basic investigation workflows
