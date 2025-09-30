# Terminal Multiplexing

## Launching screen

### Solve

**Flag:** `pwn.college{k-kOpeKzOtkVXN8Qvqxr67HGkR0.0VN4IDOxwSO5EzNzEzW}`

Basic challenge, i just had to run `screen`, and then exit it to get the flag

```
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{k-kOpeKzOtkVXN8Qvqxr67HGkR0.0VN4IDOxwSO5EzNzEzW}
hacker@terminal-multiplexing~launching-screen:~$
```

### New Learnings

The `screen` command creates a new terminal session that can run independently of the parent shell. Screen sessions continue running even if the terminal connection is lost, making them ideal for persistent workflows.

---

## Detaching and Attaching

### Solve

**Flag:** `pwn.college{wl-DpylTN5OjBejQ3OCbvPO8N4n.0lN4IDOxwSO5EzNzEzW}`

For this challenge, we had to:

1.Launch screen
2.Detach from it.
3.Run /challenge/run (this will secretly send the flag to your detached session!)
4.Reattach to see your prize

Ran `screen` then detached from it using Ctrl+A and then pressing d, ran the chall file and reattached using `screen -r`, and got the flag.

```
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{wl-DpylTN5OjBejQ3OCbvPO8N4n.0lN4IDOxwSO5EzNzEzW}
Yes! Flag is: pwn.college{wl-DpylTN5OjBejQ3OCbvPO8N4n.0lN4IDOxwSO5EzNzEzW}
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{wl-DpylTN5OjBejQ3OCbvPO8N4n.0lN4IDOxwSO5EzNzEzW}
```

### New Learnings

`Ctrl+A` followed by `d` detaches from a screen session without terminating it, while `screen -r` reattaches to the most recent detached session. Detached sessions can receive output from other processes while you're not attached, allowing for persistent background workflows.

---

## Finding Sessions

### Solve

**Flag:** `pwn.college{Ybd5qenouIuTbHc7qMQ5GriTEct.01N4IDOxwSO5EzNzEzW}`

This challenge asked us to search through all the different sessions of screen running, so I first ran `screen -ls`, then checked each of them one by one, I found the flag in `147.session_bfca6f86b1107775`

```
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
        150.pts-0.terminal-multiplexing~launching-screen        (Remote or dead)
        140.pts-0.terminal-multiplexing~detaching-and-attaching (Remote or dead)
        144.session_603ebf1e6fd893b7    (Detached)
        147.session_bfca6f86b1107775    (Detached)
        150.session_bf9291330f870c44    (Detached)
5 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ scren -r 144.session_603ebf1e6fd893b7
[screen is terminating]
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 147.session_bfca6f86b1107775
[screen is terminating]
hacker@terminal-multiplexing~finding-sessions:~$
```

### New Learnings

`screen -ls` lists all available screen sessions with their session IDs and states (Detached, Attached, or Dead). Multiple sessions can exist simultaneously, and `screen -r <session_name>` attaches to a specific session by name.

---

## Switching Windows

### Solve

**Flag:** `pwn.college{k2rJpQl_yYnt7AAUfBVaY7b0miV.0FO4IDOxwSO5EzNzEzW}`

We were asked to switch to window 0, so i ran `screen`, then used Ctrl+A 0 to switch to window 0 and got the flag.

```
hacker@terminal-multiplexing~switching-windows:~$ screen -r
[screen is terminating]
hacker@terminal-multiplexing~switching-windows:~$
```
Screen: 
```
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{k2rJpQl_yYnt7AAUfBVaY7b0miV.0FO4IDOxwSO5EzNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{k2rJpQl_yYnt7AAUfBVaY7b0miV.0FO4IDOxwSO5EzNzEzW}
hacker@terminal-multiplexing~switching-windows:~$
```

### New Learnings

Screen supports multiple windows within a single session, with `Ctrl+A` followed by a number key switching to that specific window. Window 0 is typically the first/default window, allowing you to organize different tasks within the same session.

---

## Detaching and Attaching (tmux)

### Solve

**Flag:** `pwn.college{06rC-ZVV5KWtqmlyePxHE99Ht5N.0VO4IDOxwSO5EzNzEzW}`

This challenge asked us to:
1.Launch tmux
2.Detach from it.
3.Run /challenge/run (this will send the flag to your detached session!)
4.Reattach to see your prize

So, I launched `tmux`, then detached using Ctrl+B d, then after running the chall file, reattached using `tmux a`
```
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...


Flag sent! Now reattach to your tmux session with:
  tmux attach


You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$
```
tmux:
```
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{06rC-ZVV5KWtqmlyePxHE99Ht5N.0VO4IDOxwSO5EzNzEzW}
Congratulations, here is your flag: pwn.college{06rC-ZVV5KWtqmlyePxHE99Ht5N.0VO4IDOxwSO5EzNzEzW}
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$
```

### New Learnings

Tmux is an alternative to screen with similar multiplexing capabilities, using `Ctrl+B` as the default prefix key instead of `Ctrl+A`. `Ctrl+B d` detaches from a tmux session, and `tmux a` reattaches to the most recent session with sessions numbered starting from 0.

---

## Switching Windows (tmux)

### Solve

**Flag:** `pwn.college{sV3TAjVLwy3CWsJaqRLOdm-ji99.0FM5IDOxwSO5EzNzEzW}`

This challenge asked us to navigate to windows 0 in tmux.

So i ran `tmux`, then used Ctrl+B w to get the window picker, picked window 0 and got the flag.
```
hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{sV3TAjVLwy3CWsJaqRLOdm-ji99.0FM5IDOxwSO5EzNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{sV3TAjVLwy3CWsJaqRLOdm-ji99.0FM5IDOxwSO5EzNzEzW}
hacker@terminal-multiplexing~switching-windows-tmux:~$


```
After this, i ran `chmod u=r /flag` and then `cat /flag` to get the flag.

### New Learnings

`Ctrl+B w` opens tmux's interactive window picker interface, providing a visual menu for selecting windows that's more user-friendly than screen. Like screen, tmux supports multiple windows per session with window 0 as the default, but offers better navigation through its visual interface.

# END
