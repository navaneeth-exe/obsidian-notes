
User management is a core Linux admin + cyber security skill.  
In real systems, admins create users, assign permissions, control access, and monitor accounts.

This stuff matters A LOT in:

- System Administration
    
- Ethical Hacking
    
- Privilege Escalation
    
- Server Security
    
- SOC/Blue Team work
    

---

# 1. `useradd` — Create a New User

Creates a new user account.

```bash
sudo useradd username
```

Example:

```bash
sudo useradd hacker
```

📌 This creates the user but may not create a home directory automatically.

Create with home directory:

```bash
sudo useradd -m hacker
```

---

# 2. `passwd` — Set or Change Password

Assign password to user.

```bash
sudo passwd hacker
```

Then enter password.

Example:

```text
New password:
Retype new password:
```

📌 Password won't be visible while typing.

---

# 3. `su` — Switch User

Change from one user to another.

```bash
su hacker
```

Switch to root:

```bash
su root
```

📌 Requires target user password.

Exit current user:

```bash
exit
```

---

# 4. `sudo`

Run commands as administrator/root.

```bash
sudo apt update
```

### Why Important?

Normal users have limited permissions.  
`sudo` gives temporary admin access.

Cyber security people constantly use it for:

- installing tools
    
- editing protected files
    
- managing services
    

---

# 5. `whoami`

Shows current logged-in user.

```bash
whoami
```

Example output:

```text
kali
```

---

# 6. `id`

Displays user ID information.

```bash
id
```

Example output:

```text
uid=1000(kali) gid=1000(kali) groups=1000(kali),27(sudo)
```

### Meaning

|Term|Meaning|
|---|---|
|UID|User ID|
|GID|Group ID|

---

# 7. `users`

Shows logged-in users.

```bash
users
```

---

# 8. `who`

Shows active sessions/users.

```bash
who
```

Useful for:

- monitoring logins
    
- checking remote sessions
    

---

# 9. `adduser`

More beginner-friendly way to create users.

```bash
sudo adduser navaneeth
```

It asks:

- password
    
- full name
    
- other details
    

Automatically creates:

- home directory
    
- settings
    

📌 Easier than `useradd`.

---

# 10. `userdel` — Delete User

Delete account.

```bash
sudo userdel hacker
```

Delete with home directory:

```bash
sudo userdel -r hacker
```

⚠️ `-r` removes:

- files
    
- mail
    
- home directory
    

Gone. Reduced to atoms 💀

---

# 11. `groupadd` — Create Group

Groups help manage permissions.

```bash
sudo groupadd pentesters
```

---

# 12. `groups`

Shows groups of current user.

```bash
groups
```

Example:

```text
kali sudo docker
```

---

# 13. `usermod`

Modify user account.

### Add user to group

```bash
sudo usermod -aG sudo hacker
```

### Meaning

|Option|Meaning|
|---|---|
|-a|append|
|-G|group|

This gives sudo/admin privileges.

---

# 14. `/etc/passwd`

Stores user account information.

View file:

```bash
cat /etc/passwd
```

Example entry:

```text
kali:x:1000:1000:Kali User:/home/kali:/bin/bash
```

### Structure

|Field|Meaning|
|---|---|
|kali|username|
|x|password placeholder|
|1000|UID|
|1000|GID|
|/home/kali|home directory|
|/bin/bash|shell|

---

# 15. `/etc/shadow`

Stores encrypted passwords.

```bash
sudo cat /etc/shadow
```

⚠️ Root access required.

Example:

```text
kali:$6$abcxyz...
```

📌 Passwords are hashed, not stored plain text.

Very important in:

- password auditing
    
- privilege escalation
    
- forensic analysis
    

---

# 16. `chmod` — Change Permissions

Change file access.

```bash
chmod 755 file.sh
```

### Permission Meaning

|Number|Meaning|
|---|---|
|7|rwx|
|6|rw-|
|5|r-x|
|4|r--|

---

# 17. `chown` — Change Ownership

Change file owner.

```bash
sudo chown hacker file.txt
```

Change owner + group:

```bash
sudo chown hacker:pentesters file.txt
```

---

# 18. `last`

Shows login history.

```bash
last
```

Useful for:

- incident response
    
- detecting suspicious logins
    

---

# 19. `finger` (if installed)

Displays user details.

```bash
finger hacker
```

---

# 20. `w`

Shows:

- logged-in users
    
- what they are doing
    
- system load
    

```bash
w
```

Blue team mfs love this 😭

---

# Important Concepts 🔥

## Root User

Linux super administrator.

```text
Username: root
UID: 0
```

Root can:

- access everything
    
- modify system files
    
- install/remove anything
    

---

# Types of Users

|Type|Description|
|---|---|
|Root User|Full control|
|Normal User|Limited access|
|Service/System User|Used by services/apps|

---

# File Permission Basics

```text
r = read
w = write
x = execute
```

Example:

```text
rwxr-xr-x
```

Split into:

|Section|Meaning|
|---|---|
|rwx|owner|
|r-x|group|
|r-x|others|

---

# Important Cyber Security Relevance 🛡️

User management is critical in:

|Area|Why|
|---|---|
|Privilege Escalation|Attackers target sudo/root|
|Linux Hardening|Restrict user access|
|Forensics|Track suspicious accounts|
|Server Security|Proper permission management|
|SOC Analysis|Monitor login activity|

---

# Practice Lab 💻

Try these safely in VM:

```bash
sudo adduser testuser
sudo passwd testuser
su testuser
whoami
groups
id
exit
sudo userdel -r testuser
```

---

# Common Beginner Mistakes 💀

|Mistake|Problem|
|---|---|
|Using `rm -rf` carelessly|System destruction|
|Giving everyone sudo|Security risk|
|Wrong chmod values|Exposes files|
|Editing shadow file incorrectly|System lockout|

---

# Super Important Files 📂

|File|Purpose|
|---|---|
|`/etc/passwd`|User accounts|
|`/etc/shadow`|Password hashes|
|`/etc/group`|Group info|
|`/home/username`|User files|

---

# Interview/Exam One-Liners 🎯

### What is UID?

Unique User Identifier in Linux.

### Difference between `adduser` and `useradd`?

|adduser|useradd|
|---|---|
|Interactive|Low-level|
|Easier|More manual|

### What is root user?

Linux administrator with full permissions.

[[Cyber Security Topics]]