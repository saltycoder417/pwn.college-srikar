# 1. Listing processes: 
### In this challenge, they told that they renamed hallenge/run to a random filename, and this time made it so that you cannot ls the /challenge directory. But they also launched it, so we can find it in the running process list, figure out the filename, and relaunch it directly for the flag. 

## My solve
**pwn.college{4y1wBT_DzK_5SCHw_Xr3VumRew2.QX4MDO0wiN3kjNzEzW}**

I first used the ps command to list all the running programs, but couldn't find the required program. Then i used ps command with aux argument to look at all the processes. I found a process starting with /challenge
and launched that to get the flag. 

```
hacker@processes~listing-processes:~$ ps
    PID TTY          TIME CMD
    137 pts/0    00:00:00 ssh-entrypoint
    143 pts/0    00:00:00 bash
    152 pts/0    00:00:00 ps
hacker@processes~listing-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0   1056   640 ?        Ss   08:46   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-works
root           7  0.0  0.0 231708  2560 ?        S    08:46   0:00 /run/dojo/bin/sleep 6h
root         132  0.0  0.0   4132  2560 ?        S    08:46   0:00 /challenge/23350-run-14370
root         135  0.0  0.0   2744  1600 ?        S    08:46   0:00 sleep 6h
hacker       137  0.0  0.0 231576  3520 pts/0    Ss   08:47   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-inte
hacker       143  0.0  0.0 231940  4160 pts/0    S    08:47   0:00 /run/dojo/bin/bash --login
hacker       153  0.0  0.0 233600  3840 pts/0    R+   08:47   0:00 ps aux
hacker@processes~listing-processes:~$ /challenge/23350-run-14370
Yahaha, you found me! Here is your flag:
pwn.college{4y1wBT_DzK_5SCHw_Xr3VumRew2.QX4MDO0wiN3kjNzEzW}
Now I will sleep for a while (so that you could find me with 'ps').
```

## What I learnt
I learnt about the ps command, which lists processes. By default, ps just lists the processes running in your terminal. However to make it useful (only processes running in your terminal isn't that useful), we can use either the -ef command or aux command. There are 2 syntax:
1)Standard Syntax: in this syntax, you can use -e to list "every" process and -f for a "full format" output, including arguments. These can be combined into a single argument -ef.
2) BSD Syntax: in this syntax, you can use a to list processes for all users, x to list processes that aren't running in a terminal, and u for a "user-readable" output. These can be combined into a single argument aux
These two methods, ps -ef and ps aux, result in slightly different, but cross-recognizable output.

## References
pwn.college instructions.

# 2. Killing processes: 
### In this challenge, they they told that /challenge/run will refuse to run while /challenge/dont_run is running. We must find the dont_run process and kill it, then run /challenge/run to get the flag. 

## My solve
**pwn.college{kV5jLhV3bU2OwXoV9GuAYO5YXwV.QXyQDO0wiN3kjNzEzW}**

I first used the ps command with aux argument, then connected that output with "grep dont_run" command, to find the /challenge/dont_run process. I found out the PID of that process, then i used the kill command to
terminate the process. I then ran /challenge/run to get the flag. 

```
hacker@processes~killing-processes:~$ ps aux | grep dont_run
hacker       136  0.0  0.0 231576  3520 ?        Ss   08:57   0:00 /challenge/dont_run
hacker       155  0.0  0.0 230696  2560 pts/0    S+   08:58   0:00 grep --color=auto dont_run
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{kV5jLhV3bU2OwXoV9GuAYO5YXwV.QXyQDO0wiN3kjNzEzW}
```

## What I learnt
I learnt about the kill command, which will terminate a process when we pass the PID of the process as the argument. 

## References
pwn.college instructions.

# 3. Interrupting processes: 
### In this challenge, they they told that /challenge/run will refuse to give the flag until we interrupt it.  

## My solve
**pwn.college{gzXfWOQ7gULN-Ub8SvabqKfC4uH.QXzQDO0wiN3kjNzEzW}**

I first ran /challenge/run then clicked ctrl-c at last and then entered. But that didnt work, so i ran /challenge/run and then after clicking enter, i used ctrl-c, with which i got the flag.  

```
hacker@processes~interrupting-processes:~$ /challenge/run ^C
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{gzXfWOQ7gULN-Ub8SvabqKfC4uH.QXzQDO0wiN3kjNzEzW}
```

## What I learnt
I learnt about how we can interrupt a process using ctrl-c. Ctrl-c sends an "interrupt" to whatever application is waiting on input from the terminal and, typically, this causes the application to cleanly exit.

## References
pwn.college instructions and https://catern.com/posts/terminal_quirks.html. 

# 4. Killing misbehaving processes: 
### In this challenge, they they told that there's a decoy process that's hogging a critical resource - a named pipe (FIFO) at /tmp/flag_fifo into which /challenge/run wants to write your flag. We need to kill this process, then run /challenge/run to get the flag without being overwhelmed by decoys (we don't need to redirect its output; it'll write to the FIFO on its own).

## My solve
**pwn.college{4lcle7dBRtuk0k0YKx6nkg8XynW.0FNzMDOxwiN3kjNzEzW}**

I first used the ps aux command and then redirected that output to grep /challenge/decoy to find that process using pipe operator. After i found the PID of the decoy process, i terminated/killed the process using kill command. Then i ran /challenge/run, which sent the flag to /tmp/flag_fifo. Then i read the /tmp/flag_fifo file to get the flag.  

```
hacker@processes~killing-misbehaving-processes:~$ ps aux | grep /challenge/decoy
hacker       139  0.0  0.0 230696  2560 pts/1    S+   12:44   0:00  /challenge/decoy > /tmp/flag_fifo
hacker@processes~killing-misbehaving-processes:~$ kill 139
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{4lcle7dBRtuk0k0YKx6nkg8XynW.0FNzMDOxwiN3kjNzEzW}
```

## What I learnt
I learnt how to use the ps and kill command effectively. 

## References
pwn.college instructions.

# 5. Suspending processes: 
### In this challenge, they told that this level's run wants to see another copy of itself running and using the same terminal. How? Use the terminal to launch it, then suspend it, then launch another copy while the first is suspended. 

## My solve
**pwn.college{YUuQ1B0rpR8ps6KjWPXRNtkP6VX.QX1QDO0wiN3kjNzEzW}**

I first ran /challenge/run, then i clicked ctrl-z to suspend the process. Then i ran /challenge/run again to get the flag. 

```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         146     136  0 13:10 pts/0    00:00:00 bash /challenge/run
root         148     146  0 13:10 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         146     136  0 13:10 pts/0    00:00:00 bash /challenge/run
root         153     136  0 13:10 pts/0    00:00:00 bash /challenge/run
root         155     153  0 13:10 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{YUuQ1B0rpR8ps6KjWPXRNtkP6VX.QX1QDO0wiN3kjNzEzW}
```

## What I learnt
I learned that we can suspend processes to the background using ctrl-z. 

## References
pwn.college instructions.


# 6. Resuming processes: 
### In this challenge, they told that this challenge's run needs you to suspend it, then resume it to get the flag. 

## My solve
**pwn.college{UuACM43NkrNTWpTc9V5QjZEeY2k.QX2QDO0wiN3kjNzEzW}**

I first ran /challenge/run process, then i suspended it with ctrl-z. I then resumed the process using fg command with the process as argument and got the flag. 

```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg /challenge/run
/challenge/run
I'm back! Here's your flag:
pwn.college{UuACM43NkrNTWpTc9V5QjZEeY2k.QX2QDO0wiN3kjNzEzW}
Don't forget to press Enter to quit me!
```

## What I learnt
I learned about the fg command, which is a builtin hat takes the suspended process, resumes it, and puts it back in the foreground of your terminal. 

## References
pwn.college instructions.

# 7. Backgrounding processes: 
### In this challenge, they told that this challenge's run wants to see another copy of itself running, not suspended, and using the same terminal. How? Use the terminal to launch it, then suspend it, then background it with bg and launch another copy while the first is running in the background.  

## My solve
**pwn.college{UzADlPjqi4q8HR1-2ztU8s8Elxi.QX3QDO0wiN3kjNzEzW}**

I first ran /challenge/run, then suspended the process with ctrl-z. Then i ran it in the background using the bg command and then ran the process again in the shell commandline to get the flag.

```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         146 S+   bash /challenge/run
root         148 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg /challenge/run
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.

hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         146 S    bash /challenge/run
root         156 S    sleep 6h
root         157 S+   bash /challenge/run
root         159 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{UzADlPjqi4q8HR1-2ztU8s8Elxi.QX3QDO0wiN3kjNzEzW}
```

## What I learnt
I learned about the bg command, which will basically resume the process like fg, but in the background, while fg will resume it in the foreground. This will allow the process to keep running, while giving you your shell back to invoke more commands in the meantime. 

## References
pwn.college instructions.
