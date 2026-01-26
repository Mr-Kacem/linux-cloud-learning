# File Permissions and chmod in Linux

## Overview
Linux controls access to files and directories using permissions.
Each file has an owner, a group, and a set of permission bits that define who can read, write, or execute it.

## Permission Types
- **read (r)**: view file contents or list directory contents
- **write (w)**: modify a file or create/delete files in a directory
- **execute (x)**: run a file as a program or access a directory

## Permission Scope
Permissions are defined for three categories:
- **owner (u)** – the file owner
- **group (g)** – users in the file’s group
- **others (o)** – all other users

## Viewing Permissions
```bash
ls -l filename
```
Example output: -rwxr-x---

Meaning:

- **owner**: rwx
- **group**: r-x
- **others**: ---

## Numeric (Octal) Permissions

Each permission has a numeric value:

- **read** = 4
- **write** = 2
- **execute** = 1

Combined values:

- **7** = read + write + execute (rwx)
- **6** = read + write (rw-)
- **5** = read + execute (r-x)
- **4** = read only (r--)
- **0** = no permissions (---)

Example:
``` bash
chmod 750 filename
```
Result:

- **owner**: rwx (7)
- **group**: r-x (5)
- **others**: --- (0)

## Changing Permissions
### Using numeric mode
```bash
chmod 644 filename
```
### Using symbolic mode
```bash
chmod u+x filename
chmod g-w filename
chmod o+r filename
```
### Directory Permissions (Important)

- **read**: list directory contents
- **write**: create or delete files in the directory
- **execute**: access files inside the directory

**Without execute permission on a directory, files inside cannot be accessed.**

## Notes for LFCS

- Directories almost always need execute (x) permission
- chmod -R applies permissions recursively (use with care)
- Numeric mode is faster and commonly used in exams
- Remember: permissions are evaluated as owner → group → others
