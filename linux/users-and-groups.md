# Users and Groups in Linux

## Overview
Linux is a multi-user operating system. Each process runs under a specific user and group context.
Proper user and group management is essential for security and access control.

## User Types
- **root**: superuser with full system privileges (UID 0)
- **system users**: used by services and daemons
- **regular users**: human users with limited privileges

## Important Files
- `/etc/passwd` – user account information
- `/etc/shadow` – encrypted passwords (root only)
- `/etc/group` – group definitions
- `/etc/gshadow` – secure group information

## Common Commands

### Create a user
```bash
sudo useradd -m username
```
### Create a user interactively
```bash
sudo adduser username
```
### Set or change a password
```bash
sudo passwd username
```
### Create a group
```bash
sudo groupadd groupname
```
### Add user to a group
```bash
sudo usermod -aG groupname username
```
### Chek user identity
```bash
id username
```

## Notes for LFCS
- **adduser** is a higher-level, interactive tool
- **useradd** is low-level and script-friendly
- **Always** use -aG when adding a user to a group to avoid overwriting existing groups
