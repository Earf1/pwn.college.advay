# COMPREHENDING COMMANDS

## cat: Not the pet, but the command

### Solve : 

I simply ran `cat flag` to get the flag

**Flag:** `pwn.college{sn_mZJdg5q-ATyk5HQEfgxN_lGy.QXxcTN0wSO5EzNzEzW}`

```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{sn_mZJdg5q-ATyk5HQEfgxN_lGy.QXxcTN0wSO5EzNzEzW}
hacker@commands~cat-not-the-pet-but-the-command:~$ 
```

### New Learnings

We learn about cat which is most often used for reading out files. 
It will concatenate multiple files if provided multiple arguments.
If you give no arguments at all, cat will read from the terminal input and output it.

---

## Catting absolute paths

### Solve : 

Used the absolute path directy with cat command to get the flag

**Flag:** `pwn.college{EyKPRTPY04aqt-QwfrK_8zC7vSw.QX5ETO0wSO5EzNzEzW}`

```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{EyKPRTPY04aqt-QwfrK_8zC7vSw.QX5ETO0wSO5EzNzEzW}
hacker@commands~catting-absolute-paths:~$ 
```


### New Learnings

File to be read was not in the home folder, so had to use absolute paths

---

## More catting practice

### Solve : 

I typed the command `/lib/x86_64-linux-gnu/e2fsprogs/flag` to read and retrieve the flag.

**Flag:** `pwn.college{8DNRr9r-g5ZYq5y9MsLcM5sUYCc.QXwITO0wSO5EzNzEzW}`

```
You cannot use the 'cd' command in this level, and must retrieve the flag by 
absolute path. Plus, I hid the flag in a different directory! You can find it 
in the file /lib/x86_64-linux-gnu/e2fsprogs/flag. Go cat it out **without** 
cding into that directory!
hacker@commands~more-catting-practice:~$ cat /lib/x86_64-linux-gnu/e2fsprogs/flag
pwn.college{8DNRr9r-g5ZYq5y9MsLcM5sUYCc.QXwITO0wSO5EzNzEzW}
hacker@commands~more-catting-practice:~$ 
```

### New Learnings

Again, I had to use absolute paths to retrieve the flag as cd was disabled

---

## Grepping for needle in a haystack

### Solve : 

I used the command `grep pwn.college /challenge/data.txt` to retrieve the flag.

**Flag:** `pwn.college{0nMdJxnCEpzo5ttI8oTEFAbDVcr.QX3EDO0wSO5EzNzEzW}`

```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college  /challenge/data.txt
pwn.college{0nMdJxnCEpzo5ttI8oTEFAbDVcr.QX3EDO0wSO5EzNzEzW}
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ 
```


### New Learnings

`grep` can be used when the file is too big to use `cat` on, as grep searches for the string provided.
here, the string to search was "pwn.college"

---

## Comparing Files : 

### Solve : 
used diff to compare the 2 files, and got the real flag.

**Flag :** `pwn.college{EuWPaldfT5ga3wCSrJQpjSRyxIj.01MwMDOxwSO5EzNzEzW}` 

```
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
97a98
> pwn.college{EuWPaldfT5ga3wCSrJQpjSRyxIj.01MwMDOxwSO5EzNzEzW}

```

### New Learnings : 

diff cmd can be used to find out the difference between committed file on git, and my local file.



## Listing files

### Solve : 

I ran ls /challenge and got 2 files from it, further I ran the command `/challenge/9093-renamed-run-5543` which gave me the flag:

**Flag:** `pwn.college{s5RgfuCgU0IJjBNmlauEKhJfBmp.QX4IDO0wSO5EzNzEzW}`

```
hacker@commands~listing-files:~$ ls /challenge
9093-renamed-run-5543  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/9093-renamed-run-5543
Yahaha, you found me! Here is your flag:
pwn.college{s5RgfuCgU0IJjBNmlauEKhJfBmp.QX4IDO0wSO5EzNzEzW}
```

### New Learnings :

In this challenge, we learn the `ls` command to list the files in a directory.  
`ls` will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided.

---

## Touching Files

### Solve: 
I used the command `cd /tmp` and then `touch pwn` and `touch college` to create new files in `/tmp` and ran the command `/challenge/run` to get the flag.

**Flag:** `pwn.college{wqUQmPFQ1cul-yHKPX_DQXdP77d.QXwMDO0wSO5EzNzEzW}`

```
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{wqUQmPFQ1cul-yHKPX_DQXdP77d.QXwMDO0wSO5EzNzEzW}
hacker@commands~touching-files:/tmp$ 

```

### New Learnings :

In this challenge, we had to create two files `pwn` and `college` in the tmp directory by `cd`ing into the `tmp` directory.

---

### Removing files

### Solve: 
I had to `rm delete_me` to delete the file in the `~` or /home directory and run `/challenge/check` to retrieve the flag.

**Flag:** `pwn.college{8NULquNOMOPfzB5fYrPe_j71nJ0.QX2kDM1wSO5EzNzEzW}`

```
hacker@commands~removing-files:~$ ls 
Desktop  delete_me  h
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{8NULquNOMOPfzB5fYrPe_j71nJ0.QX2kDM1wSO5EzNzEzW}
hacker@commands~removing-files:~$ 

```

### New Learnings

We learn about `rm` which removes/deletes files.

---

## Moving Files: 


### Solve:
I had to move /flag to /tmp/hack-the-planet, I achieved that using the mv command along with suitable parameters

Flag : `pwn.college{IwmgZcMB9Bx5mzlvYE2puCSCpJ6.0VOxEzNxwSO5EzNzEzW}`



```
hacker@commands~moving-files:~$ ls
Desktop  h
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{IwmgZcMB9Bx5mzlvYE2puCSCpJ6.0VOxEzNxwSO5EzNzEzW}

hacker@commands~moving-files:~$ 

```

### New Learnings : 

Used `mv` anmd learnt the parameters, the first param is the file you have to move and the second param is the location where the first file has to be moved into

---

## Hidden files

### Solve: 
I ran the command `cd /` and then ran `ls -a` to view the list of files including the hidden ones.  
I ran the command `flag-52608529479` to retrieve the flag.

**Flag:** `pwn.college{A5KiNFMfsMhGKMYGG0xw7VmYprZ.QXwUDO0wSO5EzNzEzW}`

```
hacker@commands~hidden-files:~$ ls / -a
.   .dockerenv         bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-52608529479  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:~$ cat /.flag-52608529479
pwn.college{A5KiNFMfsMhGKMYGG0xw7VmYprZ.QXwUDO0wSO5EzNzEzW}
hacker@commands~hidden-files:~$ 
```

### New Learnings

`ls` doesn't list all the files by default. Linux has a convention where files that start with a `.` don't show up by default in `ls` and in a few other contexts.  
To view them with `ls`, you need to invoke `ls` with the `-a` flag. 

---

### An Epic Filesystem Quest

### Solve : 
In this challenge I had to use basic Linux commands such as `cd, ls -a, and cat ` to navigate through directories, discover hidden files, and read clues, until finally i reached the flag.

**Flag:** `pwn.college{Awt_K6C7nf6mjcQuU3X1fuO6Vl1.QX5IDO0wSO5EzNzEzW}`

```
cd /
ls -a
cat CLUE
ls /usr/aarch64-linux-gnu/include/linux/iio
cat /usr/aarch64-linux-gnu/include/linux/iio/NUGGET-TRAPPED
cd /opt/linux/linux-5.4/Documentation/sound/designs
ls -a
cat .NOTE
ls /opt/linux/linux-5.4/drivers/pci/hotplug -a
cat /opt/linux/linux-5.4/drivers/pci/hotplug/.POINTER
ls /usr/share/racket/pkgs/redex-benchmark/redex/benchmark/models/list-machine/compiled -a
cat /usr/share/racket/pkgs/redex-benchmark/redex/benchmark/models/list-machine/compiled/.HINT
cd /usr/share/icons/hicolor/512x512/devices
ls
cat TIP
ls /opt/linux/linux-5.4/drivers/media/usb/dvb-usb-v2
cat /opt/linux/linux-5.4/drivers/media/usb/dvb-usb-v2/TRACE
cd /usr/lib/python3/dist-packages/sympy/integrals/__pycache__
ls
cat BLUEPRINT
cd /usr/share/javascript/mathjax/jax/output/SVG/fonts/Latin-Modern/Main
ls
cat GIST

```
Using all of these commands, i finally got the flag in `GIST`



### New Learnings

Always use ls -a to reveal hidden files, learnt how to run ls/cat using absolute path, also had to go with cd to move to a directory first and then run ls for some "delayed" values, also learnt to pay attention to the hints and clues given as ignoring some clues would lead to destruction of the next file.

---

### Making Directories

### Solve : 
I used `cd /tmp` to `cd` into `tmp`, then `mkdir pwn` to make a directory, `cd /tmp/pwn` to enter it, `touch college` to make a file, and ran `/challenge/check` to retrieve the flag.

**Flag:** `pwn.college{Edp8YH__EpuSM5a_myYZ2VJjkbp.QXxMDO0wSO5EzNzEzW}`

```
hacker@commands~making-directories:~$ mkdir /tmp/pwn 
hacker@commands~making-directories:~$ touch /tmp/pwn/college
hacker@commands~making-directories:~$ cd /tmp/pwn/
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{Edp8YH__EpuSM5a_myYZ2VJjkbp.QXxMDO0wSO5EzNzEzW}
hacker@commands~making-directories:/tmp/pwn$ 

```


### New Learnings

Directories can be made using `mkdir` command

---

### Finding files

### Solve : 

**Flag:** 


### New Learnings

We use the `find` command to find files.  
The `find` command takes optional arguments describing the search criteria and the search location. If you don't specify a search criteria, find matches every file. If you don't specify a search location, find uses the current working directory `(.)`.

---

### Linking files

### Solve : 

First, i ran `/challenge/catflag` , but to no avail, then i created symlink for `/home/hacker/not-the-flag` and linked it to `/flag`, now running the catflag file, gave me the flag.

**Flag:** `pwn.college{kiU8pORZx-SHg2I2fryeNrO9ZAz.QX5ETN1wSO5EzNzEzW}`
```
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
cat: /home/hacker/not-the-flag: No such file or directory
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{kiU8pORZx-SHg2I2fryeNrO9ZAz.QX5ETN1wSO5EzNzEzW}
hacker@commands~linking-files:~$ 

```

### New Learnings

Learnt about linking, both hard and soft (also symbolic)

