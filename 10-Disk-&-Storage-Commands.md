# 1. df
Displays the available and used disk space of mounted file systems.

# Syntax
df

# 2. df -h
Displays disk space in a human-readable format.

# Syntax
df -h

# Example Output
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        40G   18G   20G  48% /

# 3. du
Displays the disk usage of files and directories.

# Syntax
du

# 4. du -sh
Displays the total size of a directory in a human-readable format.

# Syntax
du -sh Documents

# Example Output
2.4G Documents

# 5. lsblk
Lists all available block storage devices and partitions.

# Syntax
lsblk

# Example Output

NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda      8:0    0   40G  0 disk
├─sda1   8:1    0   39G  0 part /
└─sda2   8:2    0    1G  0 part [SWAP]

# 6. blkid
Displays block device information such as UUID and filesystem type.

# Syntax
sudo blkid

# 7. mount
Mounts a filesystem or displays all currently mounted file systems.

# Syntax
mount

Mount a USB drive (example):

sudo mount /dev/sdb1 /mnt

# 8. umount
Safely unmounts a mounted file system.

# Syntax
sudo umount /mnt

# 9. fdisk -l
Lists all disk partitions and their details.

# Syntax
sudo fdisk -l

# Q1. What is the difference between df and du?
df shows disk space usage of the entire filesystem.

du shows disk usage of individual files and directories.

# Q2. Why is df -h preferred over df?
Because it displays sizes in a human-readable format such as KB, MB, and GB.

# Q3. What does the lsblk command display?
It displays all available block devices, including disks, partitions, and mount points.

# Q4. What is the purpose of the mount command?
It is used to mount a filesystem so that it becomes accessible through the Linux directory structure.

# Q5. What is the purpose of the umount command?
It safely disconnects a mounted filesystem before removing the storage device.

# Q6. What information does blkid provide?
It displays block device details such as UUID, LABEL, and filesystem type.

# Q7. Why is fdisk -l useful?
It lists all disk partitions and provides information such as partition size and type.