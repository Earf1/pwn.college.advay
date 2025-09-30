# Perceiving Permissions

## Changing File Ownership  

### Solve

**Flag:** `pwn.college{MN5TjGinN3KQIgJhA6V5uREzegc.QXxEjN0wSO5EzNzEzW}`

In this challenge, we were asked to change the ownership to `hacker`, so i ran `chown hacker:hacker /flag` then read the file to get the flag.

```
hacker@permissions~changing-file-ownership:~$ chown hacker:hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{MN5TjGinN3KQIgJhA6V5uREzegc.QXxEjN0wSO5EzNzEzW}
hacker@permissions~changing-file-ownership:~$
```

### New Learnings



---

## Groups and Files

### Solve

**Flag:** `pwn.college{0AJLoyehuYHiI1cb75TfTEaUbnt.QXxcjM1wSO5EzNzEzW}`

In this challenge, the /flag file was owned by the group root, so i used `chgrp` to change the group hacker, then read the file to get the flag.    

```
hacker@permissions~groups-and-files:~$ ls -l /flag
-r--r----- 1 root root 60 Sep 30 17:45 /flag
hacker@permissions~groups-and-files:~$ chgrp hacker:hacker /flag
chgrp: invalid group: ‘hacker:hacker’
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{0AJLoyehuYHiI1cb75TfTEaUbnt.QXxcjM1wSO5EzNzEzW}
hacker@permissions~groups-and-files:~$
```

### New Learnings



---

## Fun with Groups Names

### Solve

**Flag:** `pwn.college{82NvQrFBMBTPhgkDKm2N3Ff4tT-.QXycjM1wSO5EzNzEzW}`

I had to run `id` to check the groups available, then changed the group of the /flag file to `grp14465` using `chgrp`, after chaning ownership i was able to read the file, and got the flag

```
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp14465) groups=1000(grp14465)
hacker@permissions~fun-with-groups-names:~$ chgrp grp14465 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{82NvQrFBMBTPhgkDKm2N3Ff4tT-.QXycjM1wSO5EzNzEzW}
hacker@permissions~fun-with-groups-names:~$
```

### New Learnings


---

## Changing Permissions

### Solve

**Flag:** `pwn.college{QOOrt17A2qpglqmmFYOciUWrqpL.QXzcjM1wSO5EzNzEzW}`

In this challenge, i had to change the permission for /flag, to read and view using chmod, so i ran `chmod o+r /flag`, and then read the file to get the flag.


```
hacker@permissions~changing-permissions:~$ chmod o+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{QOOrt17A2qpglqmmFYOciUWrqpL.QXzcjM1wSO5EzNzEzW}
hacker@permissions~changing-permissions:~$
```

### New Learnings


---

## Executable Files

### Solve

**Flag:** `pwn.college{gt4PeDxQ6ZGeaMGBDt6GRpfXWSw.QXyEjN0wSO5EzNzEzW}`

This challenge wanted me to make the /challenge/run file executable first and then run it. I achieved this by running `chmod +x /challenge/run`

```
hacker@permissions~executable-files:~$ chmod +x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{gt4PeDxQ6ZGeaMGBDt6GRpfXWSw.QXyEjN0wSO5EzNzEzW}
hacker@permissions~executable-files:~$
```

### New Learnings


---

## Permission Tweaking Practice

### Solve

**Flag:** `pwn.college{Y6R0AuzRtlwzmKaI6YV2mopKF4M.QXwEjN0wSO5EzNzEzW}`

This challenge sucks man, anyways I had to play this game and had to change the permissions of the /challenge/pwn file, acc to whats listed in each step.
I used the following commands
```
chmod u-r /challenge/pwn
chmod u-w /challenge/pwn
chmod u=rw,g=rw,o=rw /challenge/pwn
chmod u=rw,g=r,o=rw /challenge/pwn
chmod u=rw,g=r,o=rwx /challenge/pwn
chmod u=r,g=r,o=rx /challenge/pwn
chmod u=r,g=rx,o=rx /challenge/pwn
chmod u=rwx,g=rx,o=rwx /challenge/pwn

```
After this, i ran `chmod u=r /flag` and then `cat /flag` to get the flag.

### New Learnings

The `fg` command brings suspended background jobs back to the foreground, restoring interactive control to the process.

---

## Permission Setting Practice

### Solve

**Flag:** ` `



```

```

### New Learnings


---

## The SUID Bit

### Solve

**Flag:** `pwn.college{YMLW46ZdUsj4NJ0TogZls6eKpIm.QXzEjN0wSO5EzNzEzW}`

Challenge asked us to set the SUID bit for /challenge/getroot, which i achieved by `chmod u+s /challenge/getroot`, then once i was in the shell i ran cat to get the flag.

```
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root!
Here is your shell...
root@permissions~the-suid-bit:~# cat /flag
pwn.college{YMLW46ZdUsj4NJ0TogZls6eKpIm.QXzEjN0wSO5EzNzEzW}
root@permissions~the-suid-bit:~#
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
