# 🐧 Day 1 - Navigation Commands
Navigation commands help users move through the Linux file system and manage directories efficiently.

# 1. pwd 
 Print/Present working directory
# Example

┌──(kali㉿kali)-[~]
└─$ pwd
/home/kali

# 2. ls 
 Lists the files and directories in the current directory.
# Example

┌──(kali㉿kali)-[~]
└─$ ls
abcd.txt  Documents  mno.txt    Pictures  Public     Videos
abc.txt   Downloads  Music      pqr.txt   script     xyz.txt
Desktop   first.txt  myscripts  Projects  Templates

# 3. ls -l 
 Displays a detailed (long) listing of files and directories, including permissions, owner, size, and modification date.
# Example

─(kali㉿kali)-[~]
└─$ ls -l
total 56
-rw-r--rw- 1 kali kali    0 Jul 18 11:42 abcd.txt
-rwxr-xr-x 1 kali kali   84 Jul 16 09:34 abc.txt
drwxr-xr-x 2 kali kali 4096 Jul 14 11:45 Desktop

# 4. ls -la
Displays all files and directories, including hidden files, in long listing format.
# Example

┌──(kali㉿kali)-[~]
└─$ ls -la
total 292
drwx------ 23 kali kali  4096 Jul 20 18:45 .
drwxr-xr-x  4 root root  4096 Jul 10 18:36 ..
-rw-r--rw-  1 kali kali     0 Jul 18 11:42 abcd.txt
-rwxr-xr-x  1 kali kali    84 Jul 16 09:34 abc.txt

# 5. cd
Changes the current working directory to another directory.
# Example

┌──(kali㉿kali)-[~]
└─$ cd Desktop  

┌──(kali㉿kali)-[~/Desktop]
└─$ 


# 6. cd ..	
Moves to the parent directory.
# Example

┌──(kali㉿kali)-[~/Desktop/new]
└─$ cd .. 

┌──(kali㉿kali)-[~/Desktop]
└─$ 

# 7. cd ~	
Navigates to the current user's home directory.
# Example

┌──(kali㉿kali)-[~/Desktop]
└─$ cd ~            

┌──(kali㉿kali)-[~]
└─$ 

# 8. cd /	
Navigates to the root directory of the file system.
# Example

┌──(kali㉿kali)-[~]
└─$ cd /       

┌──(kali㉿kali)-[/]
└─$ 

# 9. mkdir	
Creates a new directory.
# Example

┌──(kali㉿kali)-[~]
└─$ mkdir ABC


# 10. touch	
Creates a new empty file or updates the timestamp of an existing file.
# Example

┌──(kali㉿kali)-[~/Documents]
└─$ touch abc.txt                

┌──(kali㉿kali)-[~/Documents]
└─$ ls
abc.txt


# 11. clear	
Clears the terminal screen.
# Example 

┌──(kali㉿kali)-[~]
└─$ clear
