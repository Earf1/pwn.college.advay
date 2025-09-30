# Shell Variables
  
## Printing Variables 

### solve 

The flag : `pwn.college{o6h0SBPc3aAT5Q306AX2XMahxZM.QX3UTN0wSO5EzNzEzW}`

We had to print out the variable `FLAG` to get the flag.

I ran print on the variable with echo by running `echo $FLAG`

```
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{o6h0SBPc3aAT5Q306AX2XMahxZM.QX3UTN0wSO5EzNzEzW}
hacker@variables~printing-variables:~$ 
```

### New Learning:
Variables in bash are accessed using the `$` prefix. The `echo` command prints the value of variables to stdout. This is the fundamental way to retrieve and display stored values in shell scripts.

***

## Setting Variables

### solve 
The flag - `pwn.college{MVB8ups_rV_j2zXprlf6l2DOgyY.QX5UTN0wSO5EzNzEzW}` 

We were asked to write the value `COLLEGE` to the variable `PWN` to get the flag.

I set the `PWN` variable to `COLLEGE` by running `PWN=COLLEGE` which gave me the flag.
   
```
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{MVB8ups_rV_j2zXprlf6l2DOgyY.QX5UTN0wSO5EzNzEzW}
hacker@variables~setting-variables:~$ 
```

### New Learning:
Variable assignment in bash uses the format `VARIABLE_NAME=value` with no spaces around the equals sign. Variables are case-sensitive and typically use uppercase for environment variables.

***

## Multi-word Variables

### solve 
The flag - `pwn.college{MeS5A_EHDCUJlmoHBkhpNel4QRH.QXwYTN0wSO5EzNzEzW}`

We are supposed to write the value `COLLEGE YEAH` to the variable `PWN` to get our flag.

When the shell sees a space, it ends the variable assignment and interprets the next word as a command.
I overcame this by using quotations and running `PWN="COLLEGE YEAH"` 

```
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{MeS5A_EHDCUJlmoHBkhpNel4QRH.QXwYTN0wSO5EzNzEzW}
hacker@variables~multi-word-variables:~$ 
```

### New Learning:
Spaces in variable values must be enclosed in quotes (single or double) to prevent the shell from interpreting them as separate arguments. Double quotes allow variable expansion within the string, while single quotes treat everything literally.

---   

## Exporting Variables

### Solve
The flag : `pwn.college{EoaSp2tCSSkQ92EvCUsMpthzu9R.QXyYTN0wSO5EzNzEzW}`

We are asked to invoke `/challenge/run` with the PWN variable exported and set to the value COLLEGE, and the COLLEGE variable set to the value PWN but not exported.
So, I ran `export PWN=COLLEGE` to export the `PWN` variable and then ran `COLLEGE=PWN` to set the `COLLEGE` variable.
Then, running `/challenge/run` gave me the flag

```
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{EoaSp2tCSSkQ92EvCUsMpthzu9R.QXyYTN0wSO5EzNzEzW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```

### New Learning:
The `export` command makes variables available to child processes. Local variables (without export) are only accessible within the current shell session, while exported variables become environment variables that child processes inherit.

---

## Printing Exported Variables

### solve

the flag: `FLAG=pwn.college{oGQijslQuOiVdTK_P98JJSQP46y.QX4UTN0wSO5EzNzEzW}`

In this chall, we are asked print out all the exported variables and look for the `FLAG` variable.

I ran `env` and since there were not many exported variables, i was able to manually find the flag.

```
hacker@variables~printing-exported-variables:~$ man env
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=903c43cde888a14244480a760b853b136daf398d6c1b76e3d131c2eb39ef22eb
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{oGQijslQuOiVdTK_P98JJSQP46y.QX4UTN0wSO5EzNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
_=/run/dojo/bin/env
hacker@variables~printing-exported-variables:~$
```

### New Learning:
The `env` command displays all exported environment variables. Alternatively, `printenv` can be used for the same purpose. These commands are useful for debugging environment issues and finding specific exported variables.

---

## Storing Command Output 
### solve
The flag : `pwn.college{E19nQbKMQRnzSSVtmOb1L8WAAYF.QX1cDN1wSO5EzNzEzW}`

In this challenge, we are supposed to store the output of `/challenge/run` in a variable called `PWN` and we must print it out in order to get our flag.

I ran `PWN=$(/challenge/run)` to store the output of `/challenge/run` in `PWN`. The used `echo $PWN` to print out the flag : 

```
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{E19nQbKMQRnzSSVtmOb1L8WAAYF.QX1cDN1wSO5EzNzEzW}
hacker@variables~storing-command-output:~$
```

### New Learning:
Command substitution using `$(command)` captures the stdout of a command and assigns it to a variable. This is more modern and readable than the older backtick syntax. Useful for storing command results for later processing.

---

## Reading Input

### solve
The flag : `pwn.college{syI6AHjXmFQQdtQBxYzy9-XbEVv.QX4cTN0wSO5EzNzEzW}`

In this challenge, we are supposed to use the `read` command to write the value `COLLEGE` to the variable `PWN`.

I ran `read -p "Enter:" PWN` and then entered `COLLEGE` when prompted by the shell, which gave the flag.

```
hacker@variables~reading-input:~$ read -p "ENTER:" PWN
ENTER:COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{syI6AHjXmFQQdtQBxYzy9-XbEVv.QX4cTN0wSO5EzNzEzW}
hacker@variables~reading-input:~$
```

### New Learning:
The `read` builtin command takes user input and stores it in variables. The `-p` option displays a prompt string before reading input

--- 

## Reading Files

### solve
The flag : `pwn.college{EEtq02TeY3A5SG74c2nM6do0W-a.QXwIDO0wSO5EzNzEzW}`

In this challenge, we are supposed to read the output of `/challenge/read_me` into `PWN` to get the flag.

So i used the `<` operator we learnt from the previous to pipe the ouput of `/challenge/read_me` into the input stream of `read`. 
Running `read PWN < /challenge/read_me` gave me the flag.

```
hacker@variables~reading-files:~$ read PWN </challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{EEtq02TeY3A5SG74c2nM6do0W-a.QXwIDO0wSO5EzNzEzW}
hacker@variables~reading-files:~$
```

### New Learning:
Input redirection with `<` allows the `read` command to get input from files instead of stdin, helping us chain shell commands effectively
