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
### In this challenge, they they told that /challenge/run will refuse to run while /challenge/dont_run is running. We must find the dont_run process and kill it, then run /challenge/run to get the flag. 

## My solve
****

I first used the ps command with aux argument, then connected that output with "grep dont_run" command, to find the /challenge/dont_run process. I found out the PID of that process, then i used the kill command to
terminate the process. I then ran /challenge/run to get the flag. 

```

```

## What I learnt
I learnt about the kill command, which will terminate a process when we pass the PID of the process as the argument. 

## References
pwn.college instructions.
