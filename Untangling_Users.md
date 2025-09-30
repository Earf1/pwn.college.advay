# Untangling Users

## Becoming root with su

### Solve

**Flag:** `pwn.college{kSJASZVVqNabhMYIVNCbBlqMF9z.QX1UDN1wSO5EzNzEzW}`

As the challenge suggested, i gained root privileges by `su root` and then read the flag by `cat /flag`.

```
Connected!
hacker@users~becoming-root-with-su:~$ su root
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{kSJASZVVqNabhMYIVNCbBlqMF9z.QX1UDN1wSO5EzNzEzW}
root@users~becoming-root-with-su:/home/hacker#
```

### New Learnings

The `su` command allows switching to another user account, with `su root` being the most common way to gain root privileges.

---

## Other users with su

### Solve

**Flag:** `pwn.college{wsylzJtpwIgHwRB7izNEQXgc-y2.QX2UDN1wSO5EzNzEzW}`

In this chall, instead of root, i had to gain access to the `zardus` user which again, i gained with `su`, after gaining access to the user, i ran `/challenge/run` to get the flag.

```
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{wsylzJtpwIgHwRB7izNEQXgc-y2.QX2UDN1wSO5EzNzEzW}
zardus@users~other-users-with-su:/home/hacker$
```

### New Learnings

You can use `su <username>` to switch to any user account on the system, not just root.

---

## Cracking Passwords

### Solve

In this challenge, we had to use John the Ripper to crack the pwd of zardus, it was told that the `/etc/shadow` had a leak stored in `/challenge/shadow-leak`, so i ran `john /challenge/shadow-leak` to find the real value of the cracked hash, then ran the same cmd with `--show` to get the pwd as `aardvark`.

**Flag:** `pwn.college{k3Te5j2GzCBLz19vMmyCFuITxF8.QX3UDN1wSO5EzNzEzW}`

```
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:07 76% 1/3 0g/s 280.3p/s 280.3c/s 280.3C/s 9999945..Z9999932
0g 0:00:00:10 99% 1/3 0g/s 280.9p/s 280.9c/s 280.9C/s zardus999991915..999991900
0g 0:00:00:13 0% 2/3 0g/s 281.3p/s 281.3c/s 281.3C/s bigdog..francesco
0g 0:00:00:17 1% 2/3 0g/s 282.2p/s 282.2c/s 282.2C/s 1234qwer..babygirl
0g 0:00:00:18 1% 2/3 0g/s 282.7p/s 282.7c/s 282.7C/s katrina..karla
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04873g/s 283.7p/s 283.7c/s 283.7C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak --show
hacker:NO PASSWORD:20357:0:99999:7:::
zardus:aardvark:20361:0:99999:7:::

2 password hashes cracked, 0 left
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{k3Te5j2GzCBLz19vMmyCFuITxF8.QX3UDN1wSO5EzNzEzW}
zardus@users~cracking-passwords:/home/hacker$
```

### New Learnings

John the Ripper is a powerful password cracking tool that uses dictionary attacks and brute force methods to crack password hashes. It can work with various hash formats including those from `/etc/shadow` files. The tool shows progress with statistics like passwords per second (p/s) and completion percentage. Use `john <hashfile>` to start cracking and `john <hashfile> --show` to display already cracked passwords in a readable format.

---

## Using sudo

### Solve

**Flag:** `pwn.college{YBoDRIWs992XLJ3aEg0q_c0m8q8.QX4UDN1wSO5EzNzEzW}`

```
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{YBoDRIWs992XLJ3aEg0q_c0m8q8.QX4UDN1wSO5EzNzEzW}
hacker@users~using-sudo:~$
```

### New Learnings

The `sudo` command allows executing commands with elevated privileges without needing to switch user accounts completely.


# END
