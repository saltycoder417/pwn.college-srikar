# 1. The PATH variable: 
### In this challenge, they told that /challenge/run will delete the flag file using rm command. However, if it can't find the rm command, the flag will not be deleted, and the challenge will give it to you. Thus, you must make it so that /challenge/run can't find the rm command.

## My solve
**pwn.college{QrnzMKK0ET9rhF1xmOM0Xm1TycU.QX2cDM1wiN3kjNzEzW}**

I first blanked out the PATH variable by typying PATH=" ". Then i ran /challenge/run, and since PATH variable is blanked out, it wont be able to find rm command and hence it wont be able to delete the flag file, so i got the flag.  

```
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{QrnzMKK0ET9rhF1xmOM0Xm1TycU.QX2cDM1wiN3kjNzEzW}
```

## What I learned
I learned about the PATH variable, which is a special shell variable which stores a bunch of directory paths in which the shell will search for programs corresponding to commands. Without a PATH, bash cannot find commands like ls,rm,etc. 

## References
pwn.college instructions and https://www.linfo.org/path_env_var.html. 

# 2. Setting PATH: 
### In this challenge, they told that /challenge/run will run the win command via its bare name, but this command exists in the /challenge/more_commands/ directory, which is not initially in the PATH. The win command is the only thing that /challenge/run needs, so you can just overwrite PATH with that one directory.

## My solve
**pwn.college{QybD7cignpoCF50a1n3Fxn9Wdo0.QX1cjM1wiN3kjNzEzW}**

I overwrote PATH variable with /challenge/more_commands. Then i thought we could just run win command, but it didnt work, so i ran /challenge/run and got the flag.  

```
hacker@path~setting-path:~$ PATH=/challenge/more_commands
hacker@path~setting-path:~$ win
It looks like 'win' was improperly launched. Don't launch it directly; it MUST 
be launched by /challenge/run!
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{QybD7cignpoCF50a1n3Fxn9Wdo0.QX1cjM1wiN3kjNzEzW}
```

## What I learned
I learned how we can overwrite the PATH variable with some directory, so we can run the programs inside the directory using their bare name. Basically, by adding directories to or replacing directories in this list, you can expose these programs to be launched using their bare name. 

## References
pwn.college instructions and https://www.linfo.org/path_env_var.html. 

# 3. Finding commands: 
### In this challenge, they told that they added a win command somewhere in the PATH variable, but it wont give us the flag. However, they told that the command is in the same directory as the flag file, and they made the flag file readable for us. We have to find the directory win command and then read the flag file from there.

## My solve
**pwn.college{UnDsE5vBAqlpI6Aqtef1seFF3_z.01NzEzNxwiN3kjNzEzW}**

I first located the directroy the win command is in by using the which command, and found the directory it is in ( /challenge/paths/10466). I then read the flag file using the cat command, as they told its in the same directory as the win command. 

```
hacker@path~finding-commands:~$ which win
/challenge/paths/10466/win
hacker@path~finding-commands:~$ cat /challenge/paths/10466/flag
pwn.college{UnDsE5vBAqlpI6Aqtef1seFF3_z.01NzEzNxwiN3kjNzEzW}
```

## What I learned
I learned about the which command, which looks at each directory in PATH variable in order and prints the first file it finds whose name matches the argument you passed. When you type the name of a command, something inside one of the many directories listed in the PATH variable is what actually gets executed (unless the command is a builtin).

## References
pwn.college instructions and https://www.linfo.org/path_env_var.html. 

# 4. Adding commands: 
### In this challenge, the win command does not exist like the previous level. We have to make a shell script called win, add its location to the PATH, and enable /challenge/run to find the flag. /challenge/run runs as root and will call win. Thus, win can simply cat the flag file. 

## My solve
**pwn.college{cOkETUMTPhh5sJPNRTxI-14Hc7u.QX2cjM1wiN3kjNzEzW}**

I first located the directroy the cat command is in using which command. Then i opened the shell script of win using nano, and inside the shell script typed the absolute path of cat command and flag file as argument, this will read the flag file. I then gave access to execute the win program to everyone using chmod a+x. I then changed the PATH variable to /home/hacker, as this is where the win.sh file is in, and then ran /challenge/run to get the flag. 

```
Main terminal:
hacker@path~adding-commands:~$ which cat
/run/dojo/bin/cat
hacker@path~adding-commands:~$ nano win
hacker@path~adding-commands:~$ ls -l ./win
-rw-r--r-- 1 hacker hacker 25 Oct 11 09:02 ./win
hacker@path~adding-commands:~$ chmod a+x ./win
hacker@path~adding-commands:~$ PATH=/home/hacker
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{cOkETUMTPhh5sJPNRTxI-14Hc7u.QX2cjM1wiN3kjNzEzW}

win:
/run/dojo/bin/cat /flag

```

## What I learned
I learned how to use which command properly. I also learnt how to pass location of scripts to PATH variable, so that we can run our own commands with bare names. 

## References
pwn.college instructions (and hints) and https://www.linfo.org/path_env_var.html.

# 5. Hijacking commands: 
### In this challenge, they told that /challenge/run will will delete the flag using rm command without printing anything to us. We have to find a way to retrieve the flag.  

## My solve
**pwn.college{I-aDPrb-nXBnTvzgdRZY-GpBiJM.QX3cjM1wiN3kjNzEzW}**

I first located the directroy the cat command is in using which command. Then i opened the shell script of rm (we have to name it rm as they told that /challenge/run will delete the flag using rm, so when we run /challenge/run, it will search for the file name with rm in the PATH variable directories) using nano, and inside the shell script typed the absolute path of cat command and flag file as argument, this will read the flag file. I then gave access to execute the rm program to everyone using chmod a+x. I then changed the PATH variable to /home/hacker, as this is where our rm.sh file is in, and then ran /challenge/run to get the flag. Basically, we hijacked the /challenge/run command into giving us the flag rather than deleting it. 

```
Main terminal:
hacker@path~hijacking-commands:~$ nano rm
hacker@path~hijacking-commands:~$ ls -l ./rm
-rw-r--r-- 1 hacker hacker 25 Oct 11 09:35 ./rm
hacker@path~hijacking-commands:~$ chmod a+x ./rm
hacker@path~hijacking-commands:~$ PATH=/home/hacker
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
pwn.college{I-aDPrb-nXBnTvzgdRZY-GpBiJM.QX3cjM1wiN3kjNzEzW}

rm:
/run/dojo/bin/cat /flag

```

## What I learned
I learned that we can manipulate/hijack commands, like in this case /challenge/run to our benefits by making a shell script and naming it properly and then changing the directories of PATH variable. Also, we can put multiple directories in the PATH variable by seperating the directories with a colon (:). For example: PATH="/home/hacker:/run/dojo/bin". 

## References
pwn.college instructions (and hints) and https://www.linfo.org/path_env_var.html.

