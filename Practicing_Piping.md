# Practicing Piping

In this module, We learn to pipe.


## Redirecting output 

The flag - `pwn.college{4cdaQGLnbntBndStPrQ8KPYfZzH.QX0YTN0wSO5EzNzEzW}`

### Solve 
In this challenge, we were asked to write `PWN` to the file `COLLEGE`.

I ran `echo PWN > COLLEGE` to write the message `PWN` to the file `COLLEGE` 


```
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{4cdaQGLnbntBndStPrQ8KPYfZzH.QX0YTN0wSO5EzNzEzW}
hacker@piping~redirecting-output:~$

```

## Redirecting more output

### solve

The flag : `pwn.college{Yhk9WrFnZ8Zpy23ZFP0wlYhcZr_.QX1YTN0wSO5EzNzEzW}`

In this challenge, we are required to redirect the output of the command `/challenge/run` into a file called `myflag`.

I ran `/challenge/run > myflag` to write the output into the file `myflag` and ran `cat` to get the flag.

```
hacker@piping~redirecting-more-output:~$ /challenge/run >myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat /flag
cat: /flag: Permission denied
hacker@piping~redirecting-more-output:~$ ls /
bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hacker@piping~redirecting-more-output:~$ cd ~
hacker@piping~redirecting-more-output:~$ ls 
COLLEGE  Desktop  flag  h  myflag  not-the-flag
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{Yhk9WrFnZ8Zpy23ZFP0wlYhcZr_.QX1YTN0wSO5EzNzEzW}

hacker@piping~redirecting-more-output:~$ 
```



## Appending output

### solve 
flag :

`pwn.college{I-oTiLrk6lA6utSEKkQLI9fYtza.QX3ATO0wSO5EzNzEzW}`

To solve this challenge, we are required to redirect the output of the command `/challenge/run` in append mode (>>) to `/home/hacker/the-flag` to get the complete flag.

I ran  `/challenge/run >> /home/hacker/the-flag` to redirect the output to the file.

Then i ran `cat` on `/homehacker/the-flag` to get the flag. 

```
hacker@piping~appending-output:~$ /challenge/run >>/home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!
hacker@piping~appending-output:~$ cat /home/hacker/the-flag 
 | 
\|/ This is the first half:
 v 
pwn.college{I-oTiLrk6lA6utSEKkQLI9fYtza.QX3ATO0wSO5EzNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
hacker@piping~appending-output:~$
```
## Redirecting errors

### Solve:
flag: `pwn.college{sgfXD-gEzhoyqOew2dkGy3Yp_mj.QX3YTN0wSO5EzNzEzW}`

In this, First i ran `/challenge/run >myflag` and from the instructions it was mentioned that we had to send the stderr of `myflag` to `instructions`, after that i ran cat on myflag to get the flag.


```
hacker@piping~redirecting-errors:~$ /challenge/run >myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will check that error output is redirected to a specific file path : instructions
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!

[TEST] You should have redirected my stderr to instructions. Checking...

[FAIL] You did not satisfy all the execution requirements.
[FAIL] Specifically, you must fix the following issue:
[FAIL]   You have not redirected anything for this process' stderr.
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{sgfXD-gEzhoyqOew2dkGy3Yp_mj.QX3YTN0wSO5EzNzEzW}
hacker@piping~redirecting-errors:~$ 
```

## Redirecting input

### Solve : 
flag - `pwn.college{krhvg052LETowcj5sO3dAA4P03M.QXwcTN0wSO5EzNzEzW}`

To solve this challenge, we are required to redirect a file called `PWN` that contains `COLLEGE` to the command `/challenge/run` to get our flag.

I ran `echo COLLEGE > PWN` to create the file that we need to redirect. and then I ran `/challenge/run <PWN` to get



```
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run <PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{krhvg052LETowcj5sO3dAA4P03M.QXwcTN0wSO5EzNzEzW}
hacker@piping~redirecting-input:~$ 

```
## Grepping stored results

In this challenge, we are required to redirect the output of `/challenge/run` to `/tmp.data.txt` and then search for our flag in the data file. 

I ran the command `/challenge/run > /tmp.data.txt` to redirect the output.

The file has hundred thousand lines of text so I used grep to search for the string `pwn.college` as all the flags start with it. Then i cd to /tmp and ran  `grep pwn.college /tmp/data.txt` to get the flag

flag - `pwn.college{YlRjGdRA5vub28d2PRmUi4QTQjf.QX4EDO0wSO5EzNzEzW}`

```
hacker@piping~grepping-stored-results:~$ /challenge/run >/tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:/$ cd /tmp
hacker@piping~grepping-stored-results:/tmp$ grep pwn.college data.txt
pwn.college{YlRjGdRA5vub28d2PRmUi4QTQjf.QX4EDO0wSO5EzNzEzW}
hacker@piping~grepping-stored-results:/tmp$ 

```

## Grepping live output

### Sovle : 

The flag - `pwn.college{EE68W4-ykuH5JMtE1yT7sFY3cJ6.QX5EDO0wSO5EzNzEzW}`

like the last challenge, we are required to look for our flag in the output using the piping (|) operator.

We can run the command `/challenge/run | grep pwn.college` where `|` is the piping operator. Running this gives us

```
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college 
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{EE68W4-ykuH5JMtE1yT7sFY3cJ6.QX5EDO0wSO5EzNzEzW}
hacker@piping~grepping-live-output:~$ 

```

## Grepping errors

### solve ;

The flag - `pwn.college{8D5BqVrxzwlbVXFEqqzZuJQHSXj.QX1ATO0wSO5EzNzEzW}`

To solve this challenge, we are asked to look for our flag in the error stream of the `/challenge/run` command using grep.

This means that we can have a two-step process to grep through errors: first, we redirect standard error to standard output (2>& 1) and then pipe the now-combined stderr and stdout as normal (|)!

Combining all these cmds i ran run `/challenge/run 2>&1 | grep pwn.college`


```
hacker@piping~grepping-errors:~$ /challenge/run 2<&1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{8D5BqVrxzwlbVXFEqqzZuJQHSXj.QX1ATO0wSO5EzNzEzW}
hacker@piping~grepping-errors:~$


```


## Filtering with grep -v 

### Solve :

flag : `pwn.college{g-vMzFjDLznGil3l6uP8SaBslWF.0FOxEzNxwSO5EzNzEzW}`


Straightforward question, I ran `/challenge/run  | grep -v DECOY` to get the flag.

```
hacker@piping~filtering-with-grep-v:~$ /challenge/run  | grep -v DECOY
pwn.college{g-vMzFjDLznGil3l6uP8SaBslWF.0FOxEzNxwSO5EzNzEzW}
hacker@piping~filtering-with-grep-v:~$ 
```

### New learnings : 
-v arg allows us to filter out the part with the arg, and only get the strings which do not contain the param passed with -v.


## Duplicating piped data with tee 

### solve : 

The flag - `pwn.college{8X_1DSf5K2LyDhIcBVuWTgeqLEO.QXxITO0wSO5EzNzEzW}`

TO sovle this challenge, we are supposed to pipe the output of `/challenge/pwn` into `/challenge/college` but we also need to read the output of `/challenge/pwn` to find out the argument that will give the flag. 


We can run **`/challenge/pwn | tee data | /challenge/college`** and then `cat data` which outputs:

```
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "8X_1DSf5"
```

We can see that we must pass in the `secret` argument with the value `AFRiWxfa` into `/challenge/pwn` to get our flag. 

Running **`/challenge/pwn --secret 8X_1DSf5 | /challenge/college`** gives us 



```
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee data | /challenge/college
Processing...
WARNING: you are overwriting file data with tee's output...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat data
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "8X_1DSf5"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret 8X_1DSf5
Processing...
You must pipe the output of /challenge/pwn into /challenge/college (or 'tee' 
for debugging).
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret 8X_1DSf5 | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{8X_1DSf5K2LyDhIcBVuWTgeqLEO.QXxITO0wSO5EzNzEzW}
hacker@piping~duplicating-piped-data-with-tee:~$ 

```

### new learnings
>[!NOTE]
> We need to pipe the output into both a file and a command. We can use the `tee` command to achieve this. 
> The `tee` command duplicates data flowing through your pipes to any number of files provided on the command

## Process substitution for input 

### solve 

In this challenge we had to diff two sets of command outputs: /challenge/print_decoys, and /challenge/print_decoys_and_flag

Use process substitution with diff to compare the outputs of these two programs and find your flag
flag : `pwn.college{0ZQuFlNiFX-ezn0s2X8MVi4Qqh7.0lNwMDOxwSO5EzNzEzW}`

To solve this i just ran diff with substituting the input of the other 2 files in each step.

```
hacker@piping~process-substitution-for-input:~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
73a74
> pwn.college{0ZQuFlNiFX-ezn0s2X8MVi4Qqh7.0lNwMDOxwSO5EzNzEzW}
hacker@piping~process-substitution-for-input:~$ 

```

## Writing to multiple programs

### solve

The flag - `pwn.college{E11q5C-zuWVLfWoXdY1DaXa89A2.QXwgDN1wSO5EzNzEzW}`

To solve this challenge, we need to pipe the output of `/challenge/hack` into both `/challenge/the` and `/challenge/planet`.

The `tee` command is designed to write to files and to standard output.
We can write one of the commands as >(command) to pass it in as a file.

I ran `/challenge/hack | tee >(/challenge/the) | /challenge/planet` which will give us 



```
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) | /challenge/planet
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{E11q5C-zuWVLfWoXdY1DaXa89A2.QXwgDN1wSO5EzNzEzW}
hacker@piping~writing-to-multiple-programs:~$ 
```

## Split-piping stderr and stdout

### solve : 
The flag - `pwn.college{oXrvaZJfE-Bs7-uOAIociMz-cCZ.QXxQDM2wSO5EzNzEzW}`



To solve this challenge, we are supposed to pipe out the standard error of `/challenge/hack` into `/challenge/the` and the standard output into `/challenge/planet`

So I ran `/challenge/hack 2> >(/challenge/the) | /challenge/planet` 


```
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) | /challenge/planet
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{oXrvaZJfE-Bs7-uOAIociMz-cCZ.QXxQDM2wSO5EzNzEzW}
hacker@piping~split-piping-stderr-and-stdout:~$ 
```
## Named Pipes
### solve :
the flag: `pwn.college{w7QrPk_T1z-DQUrkJgwF5BwA1Gp.01MzMDOxwSO5EzNzEzW} `

In this challenge, the fifo file was non persistent and based on what running `/challenge/run > /tmp/flag_fifo` gave me, I opened up another terminal from the desktop and ran `cat /tmp/flag_fifo`, while keeping the run file running in the other program, and got the flag.

```
hacker@piping~named-pipes:~$ mkfifo /tmp/flag_fifo
hacker@piping~named-pipes:~$ /challenge/run > /tmp/flag_fifo
You're successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo!
Bash will now try to open the FIFO for writing, to pass it as the stdout of
/challenge/run. Recall that operations on FIFOs will *block* until both the
read side and the write side is open, so /challenge/run will not actually be
launched until you start reading from the FIFO!
```

Terminal 2 (opened from desktop):
```
hacker@piping~named-pipes:~$ cat /tmp/flag_fifo
You've correctly redirected /challenge/run's stdout to a FIFO at 
/tmp/flag_fifo! Here is your flag:
pwn.college{w7QrPk_T1z-DQUrkJgwF5BwA1Gp.01MzMDOxwSO5EzNzEzW}
```
