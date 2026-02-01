# Ownership and Special Permissions in Linux

## Overview
In Linux, each file and directory has an owner and a group.
Ownership works together with permissions to control access to system resources.

## File Ownership
Every file has:
- **user owner**
- **group owner**

Ownership determines which permission set (user or group) is applied.

## Viewing Ownership
```bash
ls -l filename
```
Example:
```bash
-rw-r----- 1 alice developers 1234 file.txt
```
Meaning:

- **owner: alice**
- **group: developers**

## Changing Ownership

**Change owner**
```bash 
sudo chown username filename
```
**Change owner and group**
```bash
sudo chown username:groupname filename
```
**Change group only**
```bash
sudo chgrp groupname filename
```
**Recursive ownership change**
```bash
sudo chown -R username:groupname directory/
```
## Special Permission Bits

**setuid (Set User ID)**

- When set on an executable file, the program runs with the owner’s privileges
- Represented by **s** in the user execute position

Example:
```bash
chmod u+s filename
```
Common example:

- /usr/bin/passwd runs as root to update /etc/shadow

**setgid (Set Group ID)**

- On files: program runs with the group’s privileges
- On directories: new files inherit the directory’s group
- Represented by **s** in the group execute position

Example:
```bash
chmod g+s directory/
```
**Sticky Bit**

- Used mainly on directories
- Only the file owner (or root) can delete files
- Represented by **t** in the others execute position

Example:
```bash
chmod +t directory/
```
Common example:

- /tmp directory

**Viewing Special Permissions**
```bash
ls -l
```
Example:
```bash
drwxrwxrwt
```

## Notes for LFCS

- **chown** usually requires root privileges
- setgid on directories is common for shared group folders
- Sticky bit prevents users from deleting each other’s files
- Special bits appear as **s** or **t** instead of **x**
