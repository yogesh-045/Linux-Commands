# 1. systemctl
Manages services and system units in Linux systems that use systemd.

# Example
systemctl status ssh

# 2. service
Legacy command used to manage services on older Linux distributions.

# Example
sudo service ssh status

# 3. journalctl
Displays logs collected by systemd.

# Example
journalctl

Latest logs:

journalctl -n 20

Follow logs in real time:

journalctl -f

# 4. Check Service Status
systemctl status apache2

Shows:

Running or Stopped

PID

Memory usage

Recent log messages

# 5. Start a Service
sudo systemctl start apache2

# 6. Stop a Service
sudo systemctl stop apache2

# 7. Restart a Service
sudo systemctl restart apache2

# 8. Enable a Service
Starts automatically after every boot.

sudo systemctl enable apache2

# 9. Disable a Service
sudo systemctl disable apache2


# Q1. What is systemctl?
systemctl is used to manage services and system units on Linux systems that use the systemd init system.

# Q2. What is the difference between systemctl and service?

systemctl is the modern command used with systemd.
service is a legacy command mainly used with older init systems, though it may still work as a compatibility wrapper.

# Q3. How do you check whether a service is running?

systemctl status <service-name>

# Q4. How do you start and stop a service?

Start:

systemctl start <service-name>

Stop:

systemctl stop <service-name>

# Q5. What is journalctl used for?
It is used to view and search logs collected by systemd, making it useful for troubleshooting services and investigating system events.