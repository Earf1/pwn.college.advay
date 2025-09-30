# Processes and Jobs

# Commands

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `ps -efww` | Lists all running processes system-wide with full command lines and detailed information | `ps -efww` |
| `ps -f` | Lists processes with full format showing UID, PID, PPID, and command | `ps -f` |
| `kill <PID>` | Terminates a process by its Process ID | `kill 136` |
| `Ctrl-C` | Sends SIGINT signal to interrupt the currently running foreground process | Press Ctrl-C while process is running |
| `Ctrl-Z` | Suspends the current foreground process and returns control to shell | Press Ctrl-Z while process is running |
| `fg` | Brings a suspended or background job back to the foreground | `fg /challenge/run` |
| `bg` | Resumes a suspended process in the background | `bg /challenge/run` |
| `command &` | Starts a command immediately in the background | `/challenge/run &` |
| `echo $?` | Displays the exit code of the last executed command | `echo $?` |
| `cat <file>` | Reads and displays the contents of a file | `cat /tmp/flag_fifo` |


## Listing Processes

### Solve

**Flag:** `pwn.college{AsL4_mgsCqWTNc7y7EmL8ecUfVX.QX4MDO0wSO5EzNzEzW}`

In this challenge, the /challenge directory was randomised, but the process was launched, so i ran `ps -efww` to list all the running processes and got the chal file as `/challenge/139-run-161` , then i just ran it to get the flag

```
hacker@processes~listing-processes:~$ ps -efww
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 14:20 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 14:20 ?        00:00:00 /run/dojo/bin/sleep 6h
root         132       1  0 14:20 ?        00:00:00 /challenge/139-run-16136
root         135     132  0 14:20 ?        00:00:00 sleep 6h
hacker       146       1  0 14:21 ?        00:00:00 /nix/store/g0q8n7xfjp7znj41hcgrq893a9m0i474-ttyd-1.7.7/bin/ttyd --port 7681 --interface 0.0.0.0 --writable -t disableLeaveAlert true /run/dojo/bin/bash --login
hacker       150       0  0 14:21 pts/0    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       156     150  0 14:21 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       165     156  0 14:21 pts/0    00:00:00 ps -efww
hacker@processes~listing-processes:~$ /challenge/139-run-16136
Yahaha, you found me! Here is your flag:
pwn.college{AsL4_mgsCqWTNc7y7EmL8ecUfVX.QX4MDO0wSO5EzNzEzW}
Now I will sleep for a while (so that you could find me with 'ps').
```

### New Learnings

The `ps -efww` command shows all processes system-wide with full command lines, making it essential for process discovery in challenges.

---

## Killing Processes

### Solve

**Flag:** `pwn.college{EbmE0uXq1DRM3VchHRYoGMOj5qY.QXyQDO0wSO5EzNzEzW}`

In this challenge, we were asked to kill `/challenge/dont_run` before running the run file, so i ran `ps -efww` to get the PID for dont_run and then killed it using `kill 136`, then ran the challenge file to get the flag.

```
hacker@processes~killing-processes:~$ ps -efww
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 14:25 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 14:25 ?        00:00:00 /run/dojo/bin/sleep 6h
root         135       1  0 14:25 ?        00:00:00 su -c /challenge/.launcher hacker
hacker       136     135  0 14:25 ?        00:00:00 /challenge/dont_run
hacker       137     136  0 14:25 ?        00:00:00 sleep 6h
hacker       139       0  0 14:25 pts/0    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       145     139  0 14:25 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       165     145  0 14:27 pts/0    00:00:00 ps -efww
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{EbmE0uXq1DRM3VchHRYoGMOj5qY.QXyQDO0wSO5EzNzEzW}
```

### New Learnings

The `kill` command terminates processes by PID, and you can find the target PID using process listing commands.

---

## Interrupting Processes

### Solve

**Flag:** `pwn.college{0gFSBbq0YRiTAVQI_JJ9UQpXfEa.QXzQDO0wSO5EzNzEzW}`

I just used "^C" to interrupt `/challenge/run`, just as the chall asked me to and got the flag

```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{0gFSBbq0YRiTAVQI_JJ9UQpXfEa.QXzQDO0wSO5EzNzEzW}
```

### New Learnings

Ctrl-C sends SIGINT signal to interrupt the currently running foreground process, providing a quick way to terminate programs.

---

## Killing Misbehaving Processes

### Solve

**Flag:** `pwn.college{gEu1optJEPT0aDAlofeMPg-sXhp.0FNzMDOxwSO5EzNzEzW}`

In this challenge, we were asked to:
1. Check what processes are running.
2. Find /challenge/decoy in the list and figure out its process ID.
3. kill it.
4. Run /challenge/run to get the flag without being overwhelmed by decoys (you don't need to redirect its output; it'll write to the FIFO on its own).

So i just ran the same cmds as before to get the PID, killed the process, then `/challenge/run` wrote the flag to `/tmp/flag_fio`, i ran cat on the file and got the flag.

```
hacker@processes~killing-misbehaving-processes:~$ ps -efww
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 14:30 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 14:30 ?        00:00:00 /run/dojo/bin/sleep 6h
root         137       1  0 14:30 ?        00:00:00 /bin/bash /challenge/.init
root         138       1  0 14:30 ?        00:00:00 /bin/bash /challenge/.init
root         140     138  0 14:30 ?        00:00:00 sleep 6h
root         141     137  0 14:30 ?        00:00:00 sleep 6h
hacker       144       0  0 14:30 pts/0    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       150     144  0 14:30 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       166     150  0 14:32 pts/0    00:00:00 ps -efww
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{gEu1optJEPT0aDAlofeMPg-sXhp.0FNzMDOxwSO5EzNzEzW}
```

### New Learnings

FIFOs (named pipes) can be used for inter-process communication, where programs write output to special files that can be read by other processes.

---

## Suspending Processes

### Solve

**Flag:** `pwn.college{UwYwojfuogdvIxckAPImp3APXQ6.QX1QDO0wSO5EzNzEzW}`

The challenge wanted the same 2 instances of the same process running, with one of them suspended, so i ran `/challenge/run` suspended it with ^Z and then ran it again to get the flag.

```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         140     129  0 14:39 pts/0    00:00:00 bash /challenge/run
root         142     140  0 14:39 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         140     129  0 14:39 pts/0    00:00:00 bash /challenge/run
root         147     129  0 14:39 pts/0    00:00:00 bash /challenge/run
root         149     147  0 14:39 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{UwYwojfuogdvIxckAPImp3APXQ6.QX1QDO0wSO5EzNzEzW}
```

### New Learnings

Ctrl-Z suspends the current process and returns control to the shell, allowing you to run multiple instances simultaneously.

---

## Resuming Processes

### Solve

**Flag:** `pwn.college{038bRUBhzE6PnoXN4o7sHOrBvRU.QX2QDO0wSO5EzNzEzW}`

Same as before, I ran the flag then suspended it. 
Then I used the builtin `fg` to resume the process.

```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg /challenge/run
/challenge/run
I'm back! Here's your flag:
pwn.college{038bRUBhzE6PnoXN4o7sHOrBvRU.QX2QDO0wSO5EzNzEzW}
Don't forget to press Enter to quit me!

Goodbye!
```

### New Learnings

The `fg` command brings suspended background jobs back to the foreground, restoring interactive control to the process.

---

## Backgrounding Processes

### Solve

**Flag:** `pwn.college{8XZjQ26ADuzr5ZZOxUywcp6kExr.QX3QDO0wSO5EzNzEzW}`

Same as before, I ran the flag then suspended it. 
Then I used the builtin `bg` to background the process, and ran another instance of run to get the flag

```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         137 S+   bash /challenge/run
root         139 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg /challenge/run
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$

Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.

hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         137 S    bash /challenge/run
root         147 S    sleep 6h
root         148 S+   bash /challenge/run
root         150 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{8XZjQ26ADuzr5ZZOxUywcp6kExr.QX3QDO0wSO5EzNzEzW}
```

### New Learnings

The `bg` command resumes suspended processes in the background, allowing them to continue execution while freeing up the terminal.

---

## Foregrounding Processes

### Solve

**Flag:** `pwn.college{AMJ41p1xP413IZLxxtphrEzD--W.QX4QDO0wSO5EzNzEzW}`

Same as before, I ran the flag then suspended it. 
Then I used the builtin `bg` to background the process and then `fg` to resume the backgrounded process and got the flag

```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg /challenge/run
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$

Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.

hacker@processes~foregrounding-processes:~$ fg /challenge/run
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{AMJ41p1xP413IZLxxtphrEzD--W.QX4QDO0wSO5EzNzEzW}
```

### New Learnings

Job control allows seamless transitions between foreground and background execution states using `fg` and `bg` commands.

---

## Starting Backgrounded Processes

### Solve

**Flag:** `pwn.college{sPeq1bYbaDYt66OQwAPKhBL5Cpy.QX5QDO0wSO5EzNzEzW}`

I just ran `/challenge/run &` as the question had mentioned to start the instance in the bg, and got the flag.

```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 138
hacker@processes~starting-backgrounded-processes:~$

Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{sPeq1bYbaDYt66OQwAPKhBL5Cpy.QX5QDO0wSO5EzNzEzW}

[1]+  Done                    /challenge/run
```

### New Learnings

Adding `&` to the end of a command immediately starts it in the background without needing to suspend first.

---

## Process Exit Codes

### Solve

**Flag:** `pwn.college{sZ4qa_sqo1WU6DIPU6KngcQPiwD.QX5YDO1wSO5EzNzEzW}`

To solve this, we were asked to get the error code of `/challenge/get-code` echo it and then submit it as an arg to `/challenge/submit-code`, so i ran the get-code program to get the error code which i echo'd using `echo $?`, and then passed it as an arg to submit-code to get the flag.

```
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
152
hacker@processes~process-exit-codes:~$ /challenge/submit-code 152
CORRECT! Here is your flag:
pwn.college{sZ4qa_sqo1WU6DIPU6KngcQPiwD.QX5YDO1wSO5EzNzEzW}
```

### New Learnings

The `$?` variable contains the exit code of the last executed command, providing essential debugging information about program execution status.

# END
