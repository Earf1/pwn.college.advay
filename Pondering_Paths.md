# PONDERING PATHS

## The Root

### Solve

Flag: `pwn.college{4Lm8e4itVagezEYRTS049RVwora.QX4cTO0wSO5EzNzEzW}`

```
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{4Lm8e4itVagezEYRTS049RVwora.QX4cTO0wSO5EzNzEzW}
hacker@paths~the-root:~$
```

### New Learnings

In this challenge we learned how to run a file using its path. To invoke it we need the complete path starting with `/` which is called the absolute path.

### References

None 

***

## Program and Absolute Path

### Solve

Flag: `pwn.college{72ikma02dqlbQpkCA6zY7.VDNoowkla0N0czW}`

The challenge program is called `run` and it is inside the `/challenge` directory. The path is `/challenge/run`. After connecting we run that exact command to get the flag.

```
hacker@paths~program-and-absolute-paths:/challenge$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{72ikma02dqlbQpkCA6zY7.VDNoowkla0N0czW}
hacker@paths~program-and-absolute-paths:/challenge$
```

### New Learnings

We learned that all challenge programs are inside the `challenge` directory and that directory itself is under `/`.

### References

None 

***

## Position Thy Self

### Solve

Flag: `pwn.college{8Atlz-hZFl7SnslcJAhSPoZOEsJ.QX2QTN0wSO5EzNzEzW}`

The program failed when I first tried `/challenge/run`. The system said I was not inside `/usr/include`. I changed into it using `cd /usr/include` and then ran `/challenge/run`. That gave the flag.

```
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /usr/include directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /usr/include
hacker@paths~position-thy-self:/usr/include$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{8Atlz-hZFl7SnslcJAhSPoZOEsJ.QX2QTN0wSO5EzNzEzW}
```

### New Learnings

We learned how to move into a directory using the `cd` command in the form `cd /path/to/place`.

### References

None 

***

## Position Elsewhere

### Solve

Flag: `pwn.college{EvqRZ-vHm-WocKCdJmjeyi9Iyuv.QX3QTN0wSO5EzNzEzW}`

The run program required me to be in `/usr/share/doc/fontconfig`. So I switched into that folder with `cd /usr/share/doc/fontconfig` and ran `/challenge/run`. That returned the flag.

```
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/doc/fontconfig directory.
hacker@paths~position-elsewhere:~$ cd /usr/share/doc/fontconfig
hacker@paths~position-elsewhere:/usr/share/doc/fontconfig$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{EvqRZ-vHm-WocKCdJmjeyi9Iyuv.QX3QTN0wSO5EzNzEzW}
hacker@paths~position-elsewhere:/usr/share/doc/fontconfig$ 
```

### New Learnings

We learned more about using `cd` to get into a required directory before running a program.

### References

None 

***

## Position Yet Elsewhere

### Solve

Flag: `pwn.college{oNdLprdYEQgzDn2k4jq8iFTv5In.QX4QTN0wSO5EzNzEzW}`

Same steps as before. Upon my first run, it told me to move to `/etc/apt/sources.list.d`, so i moved there with `cd` and then ran `/challenge/run`. It worked and gave the flag.

```
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /etc/apt/sources.list.d directory.
hacker@paths~position-yet-elsewhere:~$ cd /etc/apt/sources.list.d 
hacker@paths~position-yet-elsewhere:/etc/apt/sources.list.d$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{oNdLprdYEQgzDn2k4jq8iFTv5In.QX4QTN0wSO5EzNzEzW}
hacker@paths~position-yet-elsewhere:/etc/apt/sources.list.d$ 
```

### New Learnings

Same findings as Position Elsewhere

### References

None 

***

## Implicit Relative Paths from /

### Solve

Flag: `pwn.college{0UArlY4nbZqNSMrOh_3q3uMijOa.QX5QTN0wSO5EzNzEzW}`

Relative paths do not start with `/`. They resolve based on the current directory. For example if a file is in `/tmp/a/b/my_file` then from `/` the relative path is `tmp/a/b/my_file`. From `/tmp` the relative path is `a/b/my_file`. From `/tmp/a/b/c` it is `../my_file`.

For this challenge I went to the root with `cd /` and ran `challenge/run`. That worked.

```
hacker@paths~implicit-relative-paths-from-:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{0UArlY4nbZqNSMrOh_3q3uMijOa.QX5QTN0wSO5EzNzEzW}
```

### References

None 

***

## Explicit Relative Paths from Root

### Solve

Flag: `pwn.college{8NTWkjahjk2w7uoid-0tzUG.dBTN1QDLzQjN0czW}`

Here I was asked to use `.` for relative paths. I moved to root and used `./challenge/run`. That worked and returned the flag.

```
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{8NTWkjahjk2w7uoid-0tzUG.dBTN1QDLzQjN0czW}
```

### References

None

***

## Implicit Relative Path

### Solve

Flag: `pwn.college{ULlanlhHlpOCFrBlSxGvqljTHSW.QXxUTN0wSO5EzNzEzW}`

After moving into the `challenge` directory with `cd /challenge` I tried `run` directly. That gave an error since Linux does not run a file without explicitly mentioning its path. We must use `./run` instead. That produced the flag.

```
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ run
bash: run: command not found
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{ULlanlhHlpOCFrBlSxGvqljTHSW.QXxUTN0wSO5EzNzEzW}
```
### Learning

Learned that files can only be run after their path is explicitly mentioned

### References

None 

***

## Home Sweet Home

### Solve

Flag: `pwn.college{84XLomWf7A4rmX9YlWmTm-_XrfN.QXzMDO0wSO5EzNzEzW}`

To solve it I used `/challenge/run ~/h`. That command created and read the file giving the flag. Also I had to ensure that the argument passed was not more than 3 characters long.

```
hacker@paths~home-sweet-home:~$ /challenge/run ~/hi
The argument you provided must not have been longer than 3 characters (it's 
currently 4 characters long)!
hacker@paths~home-sweet-home:~$ /challenge/run ~/h
Writing the file to /home/hacker/h!
... and reading it back to you:
pwn.college{84XLomWf7A4rmX9YlWmTm-_XrfN.QXzMDO0wSO5EzNzEzW}
```

### Learning

Every user has a home directory under `/home`. This is where user files usually go. The `~` symbol expands to `/home/username`. In our case that is `/home/hacker`. Only the first `~` expands. For example `~/~` will become `/home/hacker/~`.

### References

None   
