# 1. apt
The primary package management tool used in Debian-based Linux distributions like Kali and Ubuntu.

# Example
sudo apt update

# 2. apt update
Downloads the latest package information from configured repositories.

# Example
sudo apt update

📌 Important: It does not install updates. It only refreshes the package list.

# 3. apt upgrade
Upgrades all installed packages to their latest available versions.

# Example
sudo apt upgrade

# 4. apt install
Installs a software package.

# Example
sudo apt install htop

# 5. apt remove
Removes an installed package but keeps its configuration files.

# Example
sudo apt remove htop

# 6. apt purge
Completely removes a package, including its configuration files.

# Example
sudo apt purge htop

# 7. apt autoremove
Removes packages that were automatically installed but are no longer needed.

# Example
sudo apt autoremove

# 8. apt search
Searches for packages available in the repositories.

# Example
apt search nmap

# 9. apt show
Displays detailed information about a package.

# Example
apt show nmap

# 10. dpkg
Manages local .deb package files directly.

# Example

Install a local package:

sudo dpkg -i package.deb

List installed packages:

dpkg -l