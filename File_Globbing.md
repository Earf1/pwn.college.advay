# File Globbing

This module tackles file globbing.

## Matching with *

### Solve :

The flag : `pwn.college{s1IpJIGWtZkJkbQiAfiT6LKr6QZ.QXxIDO0wSO5EzNzEzW}`

The first glob we'll learn is *. When it encounters a * character in any argument, the shell will treat it as "wildcard" and try to replace that argument with any files that match the pattern. The asterisk wildcard matches zero or more characters and can be used to expand file paths in bash.

In this challenge, we need to change our current working directory to `/challenge` and execute the `run` file to get our flag. However, we can only pass in 4 characters to the cd command.

I ran the command `cd /ch*` to change my current directory to `/challenge` and then ran `/challenge/run` to get the flag.

```
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{s1IpJIGWtZkJkbQiAfiT6LKr6QZ.QXxIDO0wSO5EzNzEzW}
hacker@globbing~matching-with-:/challenge$ 
```

## Matching with ?

### Solve :

Flag : `pwn.college{oY-Q2sNldlg5GdeGm7aS7Hg2Sx7.QXyIDO0wSO5EzNzEzW}`

When the shell encounters a `?` character in any argument, the shell treats it as a single character wildcard. This works like *, but only matches exactly one character.

To solve this challenge, we need to change our current directory to `/challenge` and execute the `run` file to get our flag. However, we need to use the `?` character instead of c and l in the argument to cd.

I ran the command `cd /?ha??enge` to change my current directory to `/challenge` and execute the `./run` file to get the flag.

```
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{oY-Q2sNldlg5GdeGm7aS7Hg2Sx7.QXyIDO0wSO5EzNzEzW}
hacker@globbing~matching-with-:/challenge$ 
```

## Matching with []

### Solve :
Flag : `pwn.college{cjTHzVrW7Tvjp_S0LG4U4GxYjtT.QXzIDO0wSO5EzNzEzW}`

The square brackets are essentially a limited form of ?, in that instead of matching any character, [] is a wildcard for some subset of potential characters specified within the brackets. For example, [pwn] will match the character p, w, or n.

To solve this challenge, we need to change our current directory to `/challenge/files` and execute the `run` file with a single argument that bracket globs into file_b, file_a, file_s, and file_h.

I ran `cd /challenge/files` to change my current directory to `/challenge/files`.

We can use `[]` globbing to include `file_a, file_b, file_s, file_h` so I run `/challenge/run file_[bash]` to get the flag.

```
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{cjTHzVrW7Tvjp_S0LG4U4GxYjtT.QXzIDO0wSO5EzNzEzW}
hacker@globbing~matching-with-:/challenge/files$
```

## Matching paths with []

### Solve :

Flag : `pwn.college{Mah0o9jiV0F6m9djI2G1H35Kj4q.QX0IDO0wSO5EzNzEzW}`

As with the previous challenge, we need to execute `/challenge/run` with a single argument that bracket globs into the absolute paths to the file_b, file_a, file_s, and file_h files but from our home directory.

I ran `/challenge/run/challenge/files/file_[bash]` to get the flag.

```
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{Mah0o9jiV0F6m9djI2G1H35Kj4q.QX0IDO0wSO5EzNzEzW}
hacker@globbing~matching-paths-with-:~$  
```

### New learning :
Globbing happens on a path basis, so you can expand entire paths with your globbed arguments.

## Multiple globs

### Solve :

Flag : `pwn.college{kWPE53Au_iwdZ9HRXju0kujqs5h.0lM3kjNxwSO5EzNzEzW}`

I navigated to /challenge/files and according to the challenge description I executed the following commands to get the flag:

```
hacker@globbing~multiple-globs:~$ cd /*p*
bash: cd: too many arguments
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{kWPE53Au_iwdZ9HRXju0kujqs5h.0lM3kjNxwSO5EzNzEzW}
hacker@globbing~multiple-globs:/challenge/files$ 
```

### new learning :
Bash supports the expansion of multiple globs in a single word.

## Mixing globs

### solve :
Flag : `pwn.college{wA4lwa4X3IF4waoPCDOCP9fkksP.QX1IDO0wSO5EzNzEzW}`

To solve this challenge, we need to change our current directory to `/challenge/files` and execute the `/challenge/run` file with a single argument that bracket globs into "challenging", "educational", and "pwning" files.

I ran `cd /challenge/files` to change my current directory to `/challenge/files`.

The argument had to be less than or equal to 6 characters so I first ran `/challenge/run *i*`, but was faced with the error that I did not use "[]", so I ran `/challenge/run [cpe]*` to get the flag.

```
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ ls 
amazing    challenging  educational  great  incredible  kind      magical  optimistic  queenly  splendid   uplifting   wonderful  youthful
beautiful  delightful   fantastic    happy  jovial      laughing  nice     pwning      radiant  thrilling  victorious  xenial     zesty
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run *i*
Error: you did not use a square bracket glob...
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cpe]*
You got it! Here is your flag!
pwn.college{wA4lwa4X3IF4waoPCDOCP9fkksP.QX1IDO0wSO5EzNzEzW}
hacker@globbing~mixing-globs:/challenge/files$ 
```

## Exclusionary globbing

### solve :

The flag : `pwn.college{kZYJO1a8B3IV4mb4qQu-0oyq7BW.QX2IDO0wSO5EzNzEzW}`

Sometimes, you want to filter out files in a glob. Luckily, [] helps you do this. If the first character in the brackets is a ! or (in newer versions of bash) a ^, the glob inverts, and that bracket instance matches characters that aren't listed.[7][5]

To solve this challenge, we need to change our current directory to `/challenge/files` and execute the `/challenge/run` file with a single argument that bracket globs into every file that does not start with p, w and n.

I run `cd /challenge/files` to change my current directory to `/challenge/files`.

We can use `!` to invert the glob so that it ignores the files that start with p, w and n. Therefore I first ran `/challenge/run [!pwn]`, but I had missed "*" so I ran `/challenge/run [!pwn]*` to get the flag.

```
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]
Your expansion did not expand to the requested files (amazing beautiful 
challenging delightful educational fantastic great happy incredible jovial kind 
laughing magical optimistic queenly radiant splendid thrilling uplifting 
victorious xenial youthful zesty).
Instead, it expanded to:
[!pwn]
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{kZYJO1a8B3IV4mb4qQu-0oyq7BW.QX2IDO0wSO5EzNzEzW}
hacker@globbing~exclusionary-globbing:/challenge/files$ 
```

## Tab completion

### Solve:
flag :`pwn.college{MRjVxbtfvwYgPeorB-C7jbLpeQN.0FN0EzNxwSO5EzNzEzW}`

I simply executed `cat /challenge/pwn<tab>` and tab completion expanded the path automatically.

```
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​ 
pwn.college{MRjVxbtfvwYgPeorB-C7jbLpeQN.0FN0EzNxwSO5EzNzEzW}
hacker@globbing~tab-completion:~$ 
```

## Multiple options for tab completion

### Solve :

flag : `pwn.college{0UsUMT7oQSTt7F_QMSH2vMaLu7q.0lN0EzNxwSO5EzNzEzW}`

Using tab twice to print out the multiple files and then I ran `cat /challenge/files/pwncollege-flag` to get the flag.

```
hacker@globbing~multiple-options-for-tab-completion:~$ ls /challenge/files
No ls for you in this level! Use tab-completion instead!
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwn
pwn                    pwn-the-planet         pwncollege-flag        pwncollege-flyswatter  
pwn-college            pwncollege-family      pwncollege-flamingo    pwncollege-hacking     
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-flag
pwn.college{0UsUMT7oQSTt7F_QMSH2vMaLu7q.0lN0EzNxwSO5EzNzEzW}
```

## Tab autocompletion on commands

### solve :

Flag : `pwn.college{86l4WetvawBXuuGs-8-oNLz4HG2.0VN0EzNxwSO5EzNzEzW}`

I used the same steps as tab completion, executing it directly with "pwncollege".

```
hacker@globbing~tab-completion-on-commands:~$ pwncollege-3314 
Correct! Here is your flag:
pwn.college{86l4WetvawBXuuGs-8-oNLz4HG2.0VN0EzNxwSO5EzNzEzW}
hacker@globbing~tab-completion-on-commands:~$ 
```

# END
