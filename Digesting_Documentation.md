# DIGESTING DOCUMENTATION 

in this module, we learn how to read, understand, and retrieve usable information from documentation about various linux commands.

## Challenges :

### Solve
the flag : `pwn.college{UIOsromvy8BHgfdi_hPm2Rl2JJM.QX0ITO0wSO5EzNzEzW}`

to solve this challenge, all i had to do was run the command `/challenge/challenge --giveflag` as specified in the documentation.

```
hacker@man~learning-from-documentation:/$ /challenge/challenge
Incorrect usage! You must pass an argument to me (read the challenge 
description for details).
hacker@man~learning-from-documentation:/$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{UIOsromvy8BHgfdi_hPm2Rl2JJM.QX0ITO0wSO5EzNzEzW}
hacker@man~learning-from-documentation:/$ 
```

***

## learning complex usage

### Solve

the flag :
`pwn.college{4IKZHPIJ7z4R4pR-MY9y0e3_hrQ.QX1ITO0wSO5EzNzEzW}`

in this challenge, we provide 2 arguments
which are `--printfile` and `/flag` to `/challenge/challenge` to retrieve the flag.
```
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /challenge/DESCRIPTION.md
Correct argument! Here is the /challenge/DESCRIPTION.md file:
While using most commands is straightforward, the usage of some commands can get quite complex.
For example, the arguments to commands like `sed` and `awk`, which we're definitely not getting into right now, are entire programs in an esoteric programming language!
Somewhere on the spectrum between `cd` and `awk` are commands that take arguments to their arguments...

This sounds crazy, but you've already encountered this with the `find` level in [Basic Commands](/linux-luminarium/commands).
`find` has a `-name` argument, and the `-name` argument itself takes an argument specifying the name to search for.
Many other commands are analogous.

Here is this level's documentation for `/challenge/challenge`:

> Welcome to the documentation for `/challenge/challenge`! This program allows you to print arbitrary files to the terminal, when given the `--printfile` argument. The argument to the `--printfile` argument is the path of the flag to read. For example, `/challenge/challenge --printfile /challenge/DESCRIPTION.md` will print out the description of the level!

Given that documentation, go get the flag!
hacker@man~learning-complex-usage:~$ ls -a
.  ..  .ICEauthority  .bash_history  .cache  .config  .dbus  .local  Desktop  h  not-the-flag
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /challenge/not-the-flag
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /not-the-flag
Correct argument! Here is the /not-the-flag file:
cat: /not-the-flag: No such file or directory
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{4IKZHPIJ7z4R4pR-MY9y0e3_hrQ.QX1ITO0wSO5EzNzEzW}
hacker@man~learning-complex-usage:~$ 
```

----

## reading manuals

### Solve

the flag : `pwn.college{MYy-nnuzUo9IqCconDUsLnuupto.QX0EDO0wSO5EzNzEzW}`

in this challenge, we are asked to use the `man` command to look for the flag.

so i used the `man challenge` command to get the manual :

```
hacker@man~reading-manuals:~$ man challenge

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --ynnuzo NUM
              print the flag if NUM is 900

AUTHOR
       Written by Zardus.

pwn.college                                            May 2024                                          CHALLENGE(1) 
```
thus, according to the manual i used `/challenge/challenge --ynnuzo 900` to retrieve the key.

```
hacker@man~reading-manuals:~$ /challenge/challenge --ynnuzo 900
Correct usage! Your flag: pwn.college{MYy-nnuzUo9IqCconDUsLnuupto.QX0EDO0wSO5EzNzEzW}
hacker@man~reading-manuals:~$ 
```

### new learnings

1. this level introduces the `man` command. `man` is short for manual, and will display (if available) the manual of the command you pass as an argument.

2. you can scroll around the manpage with your arrow keys and pgup/pgdn. when you're done reading the manpage, you can hit q to quit.

manpages are stored in a centralized database. if you're curious, this database lives in the `/usr/share/man` directory, but you never need to interact with it directly, you just query it using the man command. the arguments to the man command aren't file paths, but just the names of the entries themselves (e.g., you run man yes to look up the yes manpage, rather than man /usr/bin/yes, which would be the actual path to the yes program but would result in man displaying garbage).

----

## searching manuals 

### Solve

the flag : `pwn.college{8n-Vlqft0g6gKogg-Sqrz-ZxD_4.QX1EDO0wSO5EzNzEzW}`

in this challenge, i used `man challenge` to read the manual and then used above mentioned methods to navigate through the manual to obtain the flag.

after using `/flag` to search for the flag keywords i found 
```
 --zvkz
              This argument will give you the flag!
```

thus i used `/challenge/challenge --zvkz` to retrieve the flag :

```
hacker@man~searching-manuals:~$ /challenge/challenge --zvkz
Initializing...
Correct usage! Your flag: pwn.college{8n-Vlqft0g6gKogg-Sqrz-ZxD_4.QX1EDO0wSO5EzNzEzW}
hacker@man~searching-manuals:~$ 
```

### new learnings

you can scroll man pages with the arrow keys (and `pgup/pgdn`) and search with `/`. after searching, you can hit `n` to go to the next result and `n` to go to the previous result. instead of `/`, you can use `?` to search backwards!

***

## searching for manuals

### Solve 

the flag : `pwn.college{UwDFxHfclYs_xGaqlXeSwzzxJ0q.QX2EDO0wSO5EzNzEzW}`.

to solve this challenge, 
i ran the `man man` command to open up the manual for the man page database. which yielded :

```  man [man options] [[section] page ...] ...
       man -k [apropos options] regexp ...
       man -K [man options] [section] term ...
       man -f [whatis options] page ...
       man -l [man options] file ...
       man -w|-W [man options] page ...
```

i tried `man -k challenge` which got me to this :
```
hacker@man~searching-for-manuals:~$ man -k challenge
wxfclsxaql (1)       - print the flag!
```

after which i did `man wxfclsxaql` to understand its functionality. it yielded :

```
SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --wxfcls NUM
              print the flag if NUM is 020
```

thus after typing `/challenge//challenge --wxfcls 020`
, i got the flag.

```
hacker@man~searching-for-manuals:~$ /challenge/challenge --wxfcls 020
Correct usage! Your flag: pwn.college{UwDFxHfclYs_xGaqlXeSwzzxJ0q.QX2EDO0wSO5EzNzEzW}
hacker@man~searching-for-manuals:~$ 
```

### resource used
none

***

## helpful programs

### Solve

flag : `pwn.college{czYMQk5bx1Mwgpkb0PhUP5-AoEA.QX3IDO0wSO5EzNzEzW}`

i tried the command `/challenge/challenge --help` and i got this output :

```
hacker@man~helpful-programs:/challenge$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
```

after reading the "documentation/help page",
i used the command `/challenge/challenge -p`to get `510` as the value and then used the command `/challenge/challenge -g 510` to retrieve the flag.

```
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 510

hacker@man~helpful-programs:/challenge$ /challenge/challenge -g 510
Correct usage! Your flag: pwn.college{czYMQk5bx1Mwgpkb0PhUP5-AoEA.QX3IDO0wSO5EzNzEzW}
hacker@man~helpful-programs:/challenge$ 
```
### new learnings

some programs don't have a man page, but might tell you how to run them if invoked with a special argument. usually, this argument is --help, but it can often be -h or, in rare cases, -?, help, or other esoteric values like /? (though that latter is more frequently encountered on windows).

----

## help for builtins

### Solve
the flag : `pwn.college{Af2zZYCpJAcDxhWO7aZxU8MgklE.QX0ETO0wSO5EzNzEzW}`

to solve this challenge,
since `challenge` is a builtin not a command in this challenge, i used the `help <builtin>` to get some info on it,

` help challenge`

this gave me information about the function `--secret VALUE` 
which would give me the key if the `VALUE` was correct
and since the value was provided as `"Af2zZYCp"`. all i had to do was `challenge --secret Af2zZYCp` to get the flag.

```
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "Af2zZYCp".
hacker@man~help-for-builtins:~$ challenge --secret Af2zZYCp
Correct! Here is your flag!
pwn.college{Af2zZYCpJAcDxhWO7aZxU8MgklE.QX0ETO0wSO5EzNzEzW}
hacker@man~help-for-builtins:~$ 
```

### new learnings

some commands, rather than being programs with man pages and help options, are built into the shell itself. these are called builtins. builtins are invoked just like commands, but the shell handles them internally instead of launching other programs. 

# END
