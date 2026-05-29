
Most cyber security work happens in Linux environments like Kali Linux, Ubuntu, Parrot OS, etc.  
These commands are the absolute starter pack.

---

# 1. `pwd` — Print Working Directory

Shows your current folder/location.

```bash
pwd
```

Example output:

```bash
/home/kali/Desktop
```

📌 Used to know where you currently are in the filesystem.

---

# 2. `ls` — List Files and Directories

Displays files and folders.

```bash
ls
```

### Common Variations

```bash
ls -l
```

Long listing format.

```bash
ls -a
```

Shows hidden files.

```bash
ls -la
```

Shows all files with detailed info.

📌 Hidden files start with `.`

Example:

```bash
.bashrc
.hidden.txt
```

---

# 3. `cd` — Change Directory

Move between folders.

```bash
cd Downloads
```

Go back one folder:

```bash
cd ..
```

Go to home directory:

```bash
cd ~
```

📌 `..` means parent directory.

---

# 4. `mkdir` — Make Directory

Creates a folder.

```bash
mkdir test
```

Create multiple folders:

```bash
mkdir folder1 folder2
```

---

# 5. `rmdir` — Remove Empty Directory

Deletes empty folders only.

```bash
rmdir test
```

---

# 6. `rm` — Remove Files

Delete files/folders.

Delete file:

```bash
rm file.txt
```

Delete folder recursively:

```bash
rm -r foldername
```

Force delete:

```bash
rm -rf foldername
```

⚠️ Dangerous command.  
`rm -rf` can wipe entire systems if used carelessly 💀

---

# 7. `touch` — Create Empty File

```bash
touch test.txt
```

Used to create files quickly.

---

# 8. `cat` — Display File Content

```bash
cat test.txt
```

Can also create files:

```bash
cat > file.txt
```

Press:

```bash
CTRL + D
```

to save.

---

# 9. `nano` — Text Editor

Simple terminal editor.

```bash
nano notes.txt
```

### Important Shortcuts

|Shortcut|Function|
|---|---|
|CTRL + O|Save|
|CTRL + X|Exit|
|CTRL + K|Cut line|

---

# 10. `cp` — Copy Files

```bash
cp file.txt backup.txt
```

Copy folder:

```bash
cp -r folder1 folder2
```

---

# 11. `mv` — Move/Rename Files

Rename:

```bash
mv old.txt new.txt
```

Move file:

```bash
mv file.txt /home/kali/Desktop
```

---

# 12. `clear`

Clears terminal screen.

```bash
clear
```

Shortcut:

```bash
CTRL + L
```

---

# 13. `whoami`

Shows current logged-in user.

```bash
whoami
```

Example:

```bash
kali
```

---

# 14. `uname`

Shows system information.

```bash
uname
```

Detailed info:

```bash
uname -a
```

---

# 15. `ifconfig`

Shows network information.

```bash
ifconfig
```

📌 Sometimes replaced with:

```bash
ip a
```

Important in networking and pentesting.

---

# 16. `ping`

Checks network connectivity.

```bash
ping google.com
```

Stop using:

```bash
CTRL + C
```

---

# 17. `history`

Shows previously used commands.

```bash
history
```

Useful during investigations and auditing.

---

# 18. `man` — Manual Pages

Help command.

```bash
man ls
```

Shows documentation for commands.

Exit manual:

```bash
q
```

---

# 19. `sudo`

Run commands with admin/root privileges.

```bash
sudo apt update
```

📌 Stands for:

```text
Super User DO
```

---

# 20. `apt`

Package manager in Debian-based systems.

Update packages:

```bash
sudo apt update
```

Install tool:

```bash
sudo apt install nmap
```

Remove tool:

```bash
sudo apt remove nmap
```

---

# 21. `echo`

Prints text.

```bash
echo hello
```

Save text to file:

```bash
echo "hello" > file.txt
```

---

# 22. `grep`

Searches text/patterns.

```bash
grep admin users.txt
```

Very important in log analysis and forensics.

---

# 23. `find`

Search files/directories.

```bash
find /home -name test.txt
```

Useful in investigations.

---

# 24. `chmod`

Change file permissions.

```bash
chmod 777 file.txt
```

### Permission Meaning

|Number|Permission|
|---|---|
|4|Read|
|2|Write|
|1|Execute|

Example:

```text
7 = 4 + 2 + 1 = rwx
```

---

# 25. `ps`

Shows running processes.

```bash
ps
```

Detailed:

```bash
ps aux
```

Useful for malware/process analysis.

---

# 26. `kill`

Terminate processes.

```bash
kill PID
```

Force kill:

```bash
kill -9 PID
```

---

# 27. `top`

Live system monitoring.

```bash
top
```

Shows:

- CPU usage
    
- RAM usage
    
- Running processes
    

Exit:

```bash
q
```

---

# 28. `wget`

Download files from internet.

```bash
wget https://example.com/file.zip
```

---

# 29. `curl`

Transfer data from servers.

```bash
curl https://example.com
```

Very important in APIs and recon.

---

# 30. `ssh`

Remote login.

```bash
ssh user@ipaddress
```

Example:

```bash
ssh kali@192.168.1.5
```

---

# Important Cyber Security Commands 🔥

|Command|Purpose|
|---|---|
|`nmap`|Network scanning|
|`netstat`|Network connections|
|`hydra`|Password attacks|
|`wireshark`|Packet analysis|
|`aircrack-ng`|WiFi hacking|
|`sqlmap`|SQL Injection testing|

---

# Important Terminal Shortcuts

|Shortcut|Function|
|---|---|
|CTRL + C|Stop process|
|CTRL + Z|Pause process|
|CTRL + L|Clear screen|
|TAB|Auto complete|
|↑|Previous commands|

---

# Most Important Beginner Commands for Practice

Practice these daily:

```bash
pwd
ls
cd
mkdir
rm
cp
mv
cat
nano
ifconfig
ping
history
grep
find
chmod
```

---

# Beginner Practice Task 🧠

Try this:

```bash
mkdir hackinglab
cd hackinglab
touch notes.txt
nano notes.txt
cat notes.txt
cp notes.txt backup.txt
ls -la
```

This alone teaches:

- navigation
    
- file handling
    
- editing
    
- copying
    
- listing
    

Massive starter W honestly 😭🔥

[[Cyber Security Topics]]