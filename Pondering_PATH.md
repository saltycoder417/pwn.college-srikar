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
### In this challenge, they told they they added a win command somewhere in the PATH variable, but it wont give us the flag. However, they told that the command is in the same directory as the flag file, and they made the flag file readable for us. We have to find the directory win command and then read the flag file from there.

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
### In this challenge, they told they they added a win command somewhere in the PATH variable, but it wont give us the flag. However, they told that the command is in the same directory as the flag file, and they made the flag file readable for us. We have to find the directory win command and then read the flag file from there.

## My solve
****

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

