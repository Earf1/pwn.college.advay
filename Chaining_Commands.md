# Chaining Commands

## List of commands i found helpful


| Command / Operator      | Purpose / Usage Example                                   | Description                                                                 |
|------------------------|-----------------------------------------------------------|-----------------------------------------------------------------------------|
| `;`                    | `/challenge/pwn ; /challenge/college`                     | Runs commands sequentially, regardless of success/failure.                  |
| `&&`                   | `/challenge/first-success && /challenge/second`           | Runs next command only if previous succeeds (exit status 0).                |
| `||`                   | `/challenge/first-failure || /challenge/second`           | Runs next command only if previous fails (non-zero exit status).            |
| `bash script.sh`       | `bash x.sh`                                               | Executes a shell script using Bash interpreter.                             |
| `|` (pipe)             | `bash x.sh | /challenge/solve`                             | Redirects output of one command/script to another command.                  |
| `chmod +x`             | `chmod +x x`                                              | Makes a script executable.                                                  |
| `./script.sh`          | `./x`                                                     | Runs an executable script directly.                                         |
| `#!/bin/bash`          | `#!/bin/bash` at top of script                            | Shebang: tells system to use Bash to interpret the script.                  |
| `echo`                 | `echo "hack the planet"`                                 | Prints text to standard output.                                             |
| `printf`               | `printf "%s %s\n" "$2" "$1"`                           | Prints formatted output, often used for arguments.                          |
| `$1`, `$2`, ...        | `"$1"`, `"$2"`                                           | Accesses command-line arguments in scripts.                                 |
| `if [ ... ]; then ...` | `if [ "$1" = "pwn" ]; then echo "college"; fi`         | Conditional execution based on argument or test.                            |
| `elif [ ... ]; then`   | `elif [ "$1" = "learn" ]; then echo "linux";`          | Additional conditional branches in scripts.                                 |
| `else`                 | `else echo "nope"`                                       | Default case for conditionals.                                              |
| `cat`                  | `cat /challenge/run`                                      | Reads and displays contents of a file.                                      |
| `<<<`                  | `/challenge/run <<< 'hack the PLANET'`                    | Redirects a string as input to a command (here-string).                     |

***

## Chaining with semicolons

### Solve

**Flag:** `pwn.college{8Q6iJX4SsxeaAhL4OMjPhAUJR0_.QX1UDO0wSO5EzNzEzW}`

Chained `/challenge/pwn` with `/challenge/college` using `;`, as suggested by the challenge and got the flag

```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn ; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{8Q6iJX4SsxeaAhL4OMjPhAUJR0_.QX1UDO0wSO5EzNzEzW}
hacker@chaining~chaining-with-semicolons:~$
```


### New Learnings
Chaining commands with `;` lets us run multiple cmds in succession regardless of if they succeed/fail. This is useful for automation of a large number of commands.
---

## Building on Success

### Solve

**Flag:** `pwn.college{4BmPDo9SxF5RwGD2lMo3xzMGeQT.0lM0MDOxwSO5EzNzEzW}`

This challenge talked about using `&&` to chain cmds together, so i ran the 2 commands chained together and got the flag.

```
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{4BmPDo9SxF5RwGD2lMo3xzMGeQT.0lM0MDOxwSO5EzNzEzW}
hacker@chaining~building-on-success:~$
```


### New Learnings
`&&` operator only runs the successive command, if the previous command is deemed a success, i.e. if the first cmd runs only then will the successive cmds run. This is extremely helpful in compiling code

---

## Handling Failure

### Solve

**Flag:** `pwn.college{8OMYWcw1tYqvb0UbPw8ZnCFj83v.01M0MDOxwSO5EzNzEzW}`

This challenge talked about using `||` to chain cmds together, so i ran the 2 commands chained together and got the flag.

```
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{8OMYWcw1tYqvb0UbPw8ZnCFj83v.01M0MDOxwSO5EzNzEzW}
hacker@chaining~handling-failure:~$
```


### New Learnings
`||` operator only runs the successive command, if the previous command has failed, this can be used extensively in debugging the running of multiple successive commands and also for fallback commands and error handling.

---

## Your First Shell Script

### Solve

**Flag:** `pwn.college{o-hzE7LHteCvXFSgtUTBIZfsE8p.QXxcDO0wSO5EzNzEzW}`

This challenge introduced us to `.sh` files, we were asked to run /challenge/pwn followed by /challenge/college so I made a shell script with the command 
`/challenge/pwn ; /challenge/college`, then ran it with `bash` to get the flag.

```
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{o-hzE7LHteCvXFSgtUTBIZfsE8p.QXxcDO0wSO5EzNzEzW}
hacker@chaining~your-first-shell-script:~$ 
```


### New Learnings
Learned how to create a basic shell script (`.sh` file) to automate a sequence of commands. Running the script with `bash script.sh` executes all commands inside, making repetitive tasks easier and more consistent

---

## Redirecting script output

### Solve

**Flag:** `pwn.college{kdvm842J2eXbLu0x9EeAVSaQZ-A.QX4ETO0wSO5EzNzEzW}`

This challenge required us to pipe the output of `x.sh` to `/challenge/solve` to get the flag, so i used the same script as before and piped it to the solve file and got the flag.

```
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{kdvm842J2eXbLu0x9EeAVSaQZ-A.QX4ETO0wSO5EzNzEzW}
hacker@chaining~redirecting-script-output:~$ 
```


### New Learnings
Saw how to use the pipe (`|`) operator to redirect the output of one command or script into another command. This is powerful for chaining tools together, processing data, or passing results between programs.

---

## Executable Shell Scripts

### Solve

**Flag:** `pwn.college{AqwRHT61nXtKQtFYerZc-a92NBw.QX0cjM1wSO5EzNzEzW}`

Made a script which invoked /challenge/solve, then made it an executable by using chmod and ran it with `./x` without directly accessing bash. All these steps got me the flag

```
hacker@chaining~executable-shell-scripts:~$ echo -e '#!/bin/bash\n/challenge/solve' > x
hacker@chaining~executable-shell-scripts:~$ chmod +x x
hacker@chaining~executable-shell-scripts:~$ ./x
Congratulations on your shell script execution! Your flag:
pwn.college{AqwRHT61nXtKQtFYerZc-a92NBw.QX0cjM1wSO5EzNzEzW}
hacker@chaining~executable-shell-scripts:~$
```


### New Learnings
Learned to make a shell script executable using `chmod +x script.sh`, allowing it to be run directly with `./script.sh`. Adding a shebang (`#!/bin/bash`) at the top tells the system which interpreter to use, making scripts behave like standalone programs

---

## Understanding Shebangs

### Solve

**Flag:** `pwn.college{QWzbHeyDLNX4dtZj6eDP8cqgdzr.0VOzMDOxwSO5EzNzEzW}`

Challenge asked us to make a script, which has a proper shebang and outputs "hack the planet", so i used the following cmds to create the script and make it execuatable and then /challenge/run to get the flag.

```
hacker@chaining~understanding-shebangs:~$ echo -e '#!/bin/bash\necho "hack the planet"' > /home/hacker/solve.sh && chmod +x /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{QWzbHeyDLNX4dtZj6eDP8cqgdzr.0VOzMDOxwSO5EzNzEzW}

hacker@chaining~understanding-shebangs:~$ 
```

### New Learnings
**Common Shebangs**
1. #!/bin/bash for bash scripts
2. #!/usr/bin/python3 for Python scripts
3. #!/bin/sh for POSIX shell scripts --- this is a more primitive predecessor to bash with fewer features, but more compatibility to non-Linux systems!

Shebangs make linux treat the file as an interpreted program, and the contents of the rest of the line as the path to the interpreter. It then invokes the interpreter with the path to the program file as its only argument.

---

## Scripting with Arguments

### Solve

**Flag:** `pwn.college{gWlUrJPpjpwSzYxEBKidnUq4LPj.0VNzMDOxwSO5EzNzEzW}`

For this challenge, we had to write a script at /home/hacker/solve.sh that:

-Takes two arguments
-Outputs them in REVERSE order (second argument first, then the first argument).

I took 2 args by `printf "%s %s"` and then printed them in reverse order by first calling `$2` and then `$1`, then i ran /challenge/run and got the flag.

```
hacker@chaining~scripting-with-arguments:~$ echo -e '#!/bin/bash\npri
ntf "%s %s\n" "$2" "$1"' > solve.sh && chmod +x solve.sh
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{gWlUrJPpjpwSzYxEBKidnUq4LPj.0VNzMDOxwSO5EzNzEzW}
hacker@chaining~scripting-with-arguments:~$ 
```


### New Learnings
Learned how to accept command-line arguments in scripts using `$1`, `$2`, etc. This enables dynamic behavior, allowing scripts to process user input and perform actions based on provided parameters.

---

## Scripting with Conditionals

### Solve

**Flag:** `pwn.college{U5Uh9zhse4GiYEOsGf0_iFdC90K.0lNzMDOxwSO5EzNzEzW}`

For this challenge, we had to write a script at /home/hacker/solve.sh that:

-Takes one argument
-If the argument is "pwn", output "college"
-For any other input, output nothing

I took input using `printf %s` then used conditional statement if to check if the first input is pwn by `if["$1"="pwn"], if the input matched it would print "college" else print nothing, then i made the script executable and ran /challenge/run and got the flag.
```
hacker@chaining~scripting-with-conditionals:~$ printf '%s\n' '#!/bin/bash' 'if [ "$1" = "pwn" ]; then ' ' echo "college"' 'fi' > solve.sh 
hacker@chaining~scripting-with-conditionals:~$ chmod +x solve.sh
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{U5Uh9zhse4GiYEOsGf0_iFdC90K.0lNzMDOxwSO5EzNzEzW}
hacker@chaining~scripting-with-conditionals:~$ 
```


### New Learnings
Discovered how to use `if` statements in shell scripts to implement decision logic. By checking the value of arguments, scripts can perform different actions depending on input, making them more flexible and interactive

---

## Scripting with Default Case

### Solve

**Flag:** `pwn.college{4YS7eRUoX6UefThPObGiY_g4dQP.01NzMDOxwSO5EzNzEzW}`

For this challenge, we had to write a script at /home/hacker/solve.sh that:

-Takes one argument
-If the argument is "pwn", output "college"
-For any other input, output "nope"

I took input using `printf %s` then used conditional statement if to check if the first input is pwn by `if["$1"="pwn"]`, if the input matched it would print "college" else, it would print "nope", i achieved this by `'else ' ' echo "nope"'`  then i made the script executable and ran /challenge/run and got the flag.
```
hacker@chaining~scripting-with-default-cases:~$ printf '%s\n' '#!/bin/bash' 'if [ "$1" = "pwn" ]; then ' ' echo "college"' 'else ' ' echo "nope"' 
 'fi' > solve.sh 
hacker@chaining~scripting-with-default-cases:~$ chmod +x solve.sh
hacker@chaining~scripting-with-default-cases:~$ /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{4YS7eRUoX6UefThPObGiY_g4dQP.01NzMDOxwSO5EzNzEzW}
hacker@chaining~scripting-with-default-cases:~$ 
```


### New Learnings
Extended conditional logic with `else` statements, allowing scripts to provide a default response when input doesn't match expected values. This improves user feedback and script robustness


---

## Scripting with Multiple Conditons

### Solve

**Flag:** `pwn.college{IuMRlf83bWEM_sNrKH0wGAOTce1.0FOzMDOxwSO5EzNzEzW}`

For this challenge, we had to write a script at /home/hacker/solve.sh that:

-Takes one argument
-If the argument is "hack", output "the planet"
-If the argument is "pwn", output "college"
-If the argument is "learn", output "linux"
-For any other input, output "unknown"

I took input using `printf %s` then used conditional statement if to check if the first input is hack by `if["$1"="pwn"]`, if the input matched it would print "the planet" else if, input is "pwn it would print "college", `elif [ "$1" = "pwn" ]; then echo "college";`, similiarly i did the same for if the input is "learn" it would print "linux", and finally for any other input, it would print "unknown", `else echo "unknown";`. 
Then again i made the script executable and ran /challenge/run to get the flag.

```
hacker@chaining~scripting-with-multiple-conditions:~$ printf '%s\n' '#!/bin/bash' 'if [ "$1" = "hack" ]; then echo "the planet"; elif [ "$1" = "pwn" ]; then echo "college"; elif [ "$1" = "learn" ]; then echo "linux"; else echo "unknown"; fi' > /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ chmod +x solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{IuMRlf83bWEM_sNrKH0wGAOTce1.0FOzMDOxwSO5EzNzEzW}
hacker@chaining~scripting-with-multiple-conditions:~$ 
```


### New Learnings
Learned to use `elif` for handling multiple input scenarios in scripts. This enables scripts to respond to several specific cases and provide a fallback for unknown inputs, making them more comprehensive and user-friendly.

---

## Reading shell scripts

### Solve

**Flag:** `pwn.college{EoiKMYugOh-bW7iitKIA9E1xAy1.0lMwgDOxwSO5EzNzEzW}`

For this challenge, the /challenge/run file required a password, which was harcoded into it.
So i ran cat on the file, and got to know that the flag is "hack the PLANET", so i just passed that to the file using `/challenge/run <<< 'hack the PLANET'`, and got the flag

```
hacker@chaining~reading-shell-scripts:~$ cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ /challenge/run <<< 'hack the PLANET'
CORRECT! Your flag:
pwn.college{EoiKMYugOh-bW7iitKIA9E1xAy1.0lMwgDOxwSO5EzNzEzW}
hacker@chaining~reading-shell-scripts:~$ 
```


### New Learnings
Practiced reading and understanding shell scripts using tools like `cat`. This skill is essential for debugging, reverse engineering, and solving CTF challenges, as it helps you find hardcoded values, passwords, or logic errors in scripts.


# END
