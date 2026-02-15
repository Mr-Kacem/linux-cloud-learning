# Processes and Signals in Linux

### Overview
A process is a running instance of a program.
Each process has a unique Process ID (PID) and runs under a specific user context.

## Viewing Processes

### List processes
```bash
ps
```
### Detailed process list
``` bash
ps aux
```
### Tree view of processes
``` bash
ps -ef --forest
```
### Real-time process monitoring
``` bash
top
```
### Process States

Common states include:

- R: Running
- S: Sleeping
- T: Stopped
- Z: Zombie


## Managing Processes

### Kill a process by PID
``` bash
kill PID
```
### Force kill a process
``` bash
kill -9 PID
```
### Kill by name
``` bash
killall processname
```


## Signals

Signals are used to control processes.

Common signals:

- SIGTERM (15): graceful termination (default)
- SIGKILL (9): force termination
- SIGHUP (1): reload configuration
- SIGSTOP (19): pause a process
- SIGCONT (18): resume a paused process

List signals:
``` bash
kill -l
```


## Foreground and Background Processes

Run in background:
``` bash
command &
```
Bring background job to foreground:
``` bash
fg
```
List jobs:
``` bash
jobs
```


## Process Priority
### Start process with priority
``` bash
nice -n 10 command
```
### Change priority of running process
``` bash
renice 5 PID
```
Lower nice value = higher priority


### Notes for LFCS

- Always try SIGTERM before SIGKILL
- Zombie processes cannot be killed directly (parent must handle them)
- Use **ps aux | grep processname** to locate processes quickly
- **top** helps identify high CPU or memory usage
