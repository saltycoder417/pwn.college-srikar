# 1. Launching screen: 
### In this challenge, they asked us launch screen to get the flag. 

## My solve
**pwn.college{A3NiUy82xIBDlGHSWzKzvZDfZOL.QXxEjN0wiN3kjNzEzW}**

I launched a new screen session, using "screen" and got the flag. 

```
hacker@terminal-multiplexing~launching-screen:~$ screen
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{gKO7RfmtK-5cPY__-XXKDXpN60x.0VN4IDOxwiN3kjNzEzW}
```

## What I learned
I learned about screen. Screen is a program that creates virtual terminals inside your terminal. It's somewhat like having multiple browser tabs, but for your command line. To start a screen, we just have to type "screen" on the commandline. When you're done with your command line, type exit or press Ctrl-D to leave the screen session. Then screen will terminate and return you to your original shell.

## References
pwn.college instructions. 

# 2. Detaching and attaching: 
### In this challenge, they asked us to first launch a screen, then detach from it and run /challenge/run. This will send the flag to the detached screen/session. We have to reattach to the screen to get the flag.

## My solve
**pwn.college{gdql9pCtpv6qa_El9_J6cyrsLC3.0lN4IDOxwiN3kjNzEzW}**

I first launched a new session using screen. After entering the session, i detached from it using ctrl-A and then pressing d (after releasing ctrl-A), and ran /challenge/run in the main terminal. I then again went back to the screen using "screen -r" and found the flag in the session. 

```
main terminal:
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen
[detached from 147.pts-0.terminal-multiplexing~detaching-and-attaching]
hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run
Found detached screen session: 147.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...

Flag sent! Now reattach to your screen session with:

  screen -r

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r
[detached from 147.pts-0.terminal-multiplexing~detaching-and-attaching]

screen:
hacker@terminal-multiplexing~detaching-and-attaching:~$
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{gdql9pCtpv6qa_El9_J6cyrsLC3.0lN4IDOxwiN3kjNzEzW}
Yes! Flag is: pwn.college{gdql9pCtpv6qa_El9_J6cyrsLC3.0lN4IDOxwiN3kjNzEzW}
```

## What I learned
I learned how we can come out (detach) and go back (attach) to the screen session. We can detach from a screen by first pressing ctrl-A, releasing it and then pressing d. This leaves your session running in the background while you return to your normal terminal. We can go back to the session (reattach) by typing "screen -r" on the commandline. 

## References
pwn.college instructions. 

# 3. Finding sessions: 
### In this challenge, they told that they created three different screens, of which 1 of them has the flag, and other 2 are decoys. We need to check each one until we find the flag.

## My solve
**pwn.college{A_vBAsEyUsAyEISJc4Q8LpgB3jp.01N4IDOxwiN3kjNzEzW}**

In the main terminal, i first used screen -ls to list all the screens. I then used "screen -r PID" to go into different sessions. First session with PID 144 was a decoy. The session with PID 147 had the flag.  I ignored the sessions which told remote or dead. 

```
Main terminal:
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
        158.pts-0.terminal-multiplexing~launching-screen        (Remote or dead)
        147.pts-0.terminal-multiplexing~detaching-and-attaching (Remote or dead)
        144.session_d6600d1ce9e418b3    (Detached)
        147.session_d76ea64ef0446873    (Detached)
        150.session_0caae556c7fa8f89    (Detached)
5 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 144
[detached from 144.session_d6600d1ce9e418b3]
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 147
Remove dead screens with 'screen -wipe'.
[detached from 147.session_d76ea64ef0446873]
session with flag:
hacker@terminal-multiplexing~finding-sessions:~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{A_vBAsEyUsAyEISJc4Q8LpgB3jp.01N4IDOxwiN3kjNzEzW}
pwn.college{A_vBAsEyUsAyEISJc4Q8LpgB3jp.01N4IDOxwiN3kjNzEzW}
```

## What I learned
I learned that we can list sessions using "screen -ls". To go into a specific session, we have to keep the PID of the session at the end of session -r (session -r PID). 

## References
pwn.college instructions. 

# 4. Switching windows: 
### In this challenge, they told that they have created two windows in a sission. window 0 has the flag and window 1 has a welcome message. We have to go to window 0 to get the flag.

## My solve
** pwn.college{YSQ94w-zEsybTGDSDzSi7V6NrbN.0FO4IDOxwiN3kjNzEzW}**

In the main terminal, i first used screen -ls to find the PID of the session. After that i entered the session using screen -r 135. Then i went to window 0 using ctrl-A and then 0 and found the flag. 

```
Main terminal:
hacker@terminal-multiplexing~switching-windows:~$ screen -ls
There are screens on:
        158.pts-0.terminal-multiplexing~launching-screen        (Remote or dead)
        147.pts-0.terminal-multiplexing~detaching-and-attaching (Remote or dead)
        144.session_d6600d1ce9e418b3    (Remote or dead)
        147.session_d76ea64ef0446873    (Remote or dead)
        150.session_0caae556c7fa8f89    (Remote or dead)
        135.challenge_session   (Detached)
6 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~switching-windows:~$ screen -r 135
[detached from 135.challenge_session]

window 1:
 cat <<MSG
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!
MSG
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Welcome to the window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-A 0 to switch to window 0!
> MSG
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!

window 0:
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{YSQ94w-zEsybTGDSDzSi7V6NrbN.0FO4IDOxwiN3kjNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{YSQ94w-zEsybTGDSDzSi7V6NrbN.0FO4IDOxwiN3kjNzEzW}
```

## What I learned
I learned that a screen session can have multiple windows. To control through windows, we can use different keyboard shortcuts, all starting with Ctrl-A:

Ctrl-A c - Create a new window

Ctrl-A n - Next window

Ctrl-A p - Previous window

Ctrl-A 0 through Ctrl-A 9 - Jump directly to window 0-9

Ctrl-A " - bring up a selection menu of all of the windows

## References
pwn.college instructions. 

# 5. Detaching and attaching (tmux): 
### In this challenge, they asked us to first launch tmux, then detach from it, then run /challenge/run in the main terminal, which will send the flag to your detached session, then reattach to the session to get the flag. 

## My solve
**pwn.college{gEkIlzgfrpgN-mVneOgRi-Ds5C_.0VO4IDOxwiN3kjNzEzW}**

I launched a new session using tmux, then i detached from the session using ctrl-B and then d (after releasing ctrl-B), and then ran /challenge/run in the main terminal. Then the flag was printed in the session, so i went back to the session using "tmux a" and got the flag. 

```
Main terminal:
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a-
unknown command: a-
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a
[detached (from session 0)]

tmux:
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{gEkIlzgfrpgN-mVneOgRi-Ds5C_.0VO4IDOxwiN3kjNzEzW}
Congratulations, here is your flag: pwn.college{gEkIlzgfrpgN-mVneOgRi-Ds5C_.0VO4IDOxwiN3kjNzEzW}
```

## What I learned
I learned about terminal multiplexer (tmux) which is similar to screen, but with different key bindings. The biggest difference between them is that tmux uses ctrl-B as its command prefix while screen uses ctrl-A. 

To detach from tmux- ctrl-B followed by d.

tmux ls - List sessions

tmux attach or tmux a - Reattach to session

## References
pwn.college instructions. 


# 6. Switching windows (tmux): 
### In this challenge, they told that they created a tmux session with 2 windows, window 1 has a welcome message, and window 0 has the flag. We have to go to window 0 to get the flag. 

## My solve
**pwn.college{EZ8P2JLM0gJsLJmaD_03Ckr_8LJ.0FM5IDOxwiN3kjNzEzW}**

I first listed all the tmux sessions using tmus ls. Since there was only 1 session, i entered it using tmux a. Then i went to window 0 using ctrl-B and 0 (after releasing ctrl-B) and found the flag. 

```
Main terminal:
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux ls
challenge_session: 2 windows (created Fri Oct 10 17:46:41 2025)
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux a
[detached (from session challenge_session)]

Window 1:
 cat <<MSG
Welcome to the tmux window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-B 0 to switch to window 0!
MSG
hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Welcome to the tmux window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-B 0 to switch to window 0!
> MSG
Welcome to the tmux window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-B 0 to switch to window 0!

window 0:
hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{EZ8P2JLM0gJsLJmaD_03Ckr_8LJ.0FM5IDOxwiN3kjNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{EZ8P2JLM0gJsLJmaD_03Ckr_8LJ.0FM5IDOxwiN3kjNzEzW}
```

## What I learned
I learned how we can navigate windows in tmux: 

Ctrl-B c - Create a new window

Ctrl-B n - Next window

Ctrl-B p - Previous window

Ctrl-B 0 through Ctrl-B 9 - Jump to window 0-9

Ctrl-B w - See a nice window picker

Tmux also shows your windows at the bottom in a status bar.  

## References
pwn.college instructions. 
