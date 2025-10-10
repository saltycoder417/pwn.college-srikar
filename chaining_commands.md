# 1. Chaining with semicolons: 
### In this challenge, they asked us to run /challenge/pwn and then /challenge/college, chaining them with a semicolon.

## My solve
**pwn.college{A_NZihqZd1BC4hQxZiqez6Mfr4E.QX1UDO0wiN3kjNzEzW}**

I ran /challenge/pwn and /challenge/college programs chained with a semicolon (;) to get the flag.

```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{A_NZihqZd1BC4hQxZiqez6Mfr4E.QX1UDO0wiN3kjNzEzW}
```

## What I learnt
I learned that we can chain commands with a semicolon (;). In most contexts, ; separates commands in a similar way to how Enter separates lines.

## References
pwn.college instructions.  

# 2. Building on success: 
### In this challenge, they asked us to chain the programs /challenge/first-success and /challenge/second using the "&&" operator.

## My solve
**pwn.college{I7wyRTbVKnfwWafsLSWRJwFgKgZ.0lM0MDOxwiN3kjNzEzW}**

I ran /challenge/first-success along with the AND operator (&&) and /challenge/second (/challenge/first-success && /challenge/second) to get the flag. 

```
hacker@chaining~building-on-success:~$ /challenge/first-success
hacker@chaining~building-on-success:~$ echo $?
0
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{I7wyRTbVKnfwWafsLSWRJwFgKgZ.0lM0MDOxwiN3kjNzEzW}
```

## What I learnt
I learned about the "&&" operator. It allows us to run a second command only if the first command succeeds (in Linux convention, this means it exited with code 0). syntax: "command1 && command2", this means run command1, and if it succeeds then run command2.  

## References
pwn.college instructions.  

# 3. Handling failure: 
### In this challenge, they asked us to chain the programs /challenge/first-failure and /challenge/second using the OR operator (||). 

## My solve
**pwn.college{A-5st5ivNQ3Jj49bq8o8hTtMukG.01M0MDOxwiN3kjNzEzW}**

I ran /challenge/first-failure along with the OR operator (||) and /challenge/second (/challenge/first-failure || /challenge/second) to get the flag. 

```
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{A-5st5ivNQ3Jj49bq8o8hTtMukG.01M0MDOxwiN3kjNzEzW}
```

## What I learnt
I learned about the OR (||) operator. It allows us to run a second command only if the first command fails (in Linux convention, this means it exited with a non zero code ). syntax: "command1 || command2", this means run command1, and if it fails then run command2.  

## References
pwn.college instructions.

# 4. Your first shell script: 
### In this challenge, they told us to run /challenge/pwn and then /challenge/college, but in a shell script, and then run it with bash to get the flag. 

## My solve
**pwn.college{QUxQ_7R14fHyEoH3z2JICKAkjps.QXxcDO0wiN3kjNzEzW}**

I used nano command to create a shell script named x.sh, and inside nano i typed /challenge/pwn && /challenge/college. Then i launched x.ch using bash command in the main terminal and got the flag. 

```
hacker@chaining~your-first-shell-script:~$ nano x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{QUxQ_7R14fHyEoH3z2JICKAkjps.QXxcDO0wiN3kjNzEzW
```

## What I learnt
I learned how to make a shell script. They generally end with .sh and Linux has nano, which is a commandline text editor which we can use to make or edit shell scripts. To open a shell script in nano, we have to type "nano FILENAME" on the commandline. We have to use bash command to execute the file. When we use bash command, the shell reads commands from the file rather than the user.  

## References
pwn.college instructions.

# 5. Redirecting script output: 
### In this challenge, they told us create a script that calls the /challenge/pwn command followed by the /challenge/college command, and pipe the output of the script into a single invocation of the /challenge/solve command. 

## My solve
**pwn.college{MrvTzQumZqn0s3DqJUuFAB93jbY.QX4ETO0wiN3kjNzEzW}**

I used nano command to create a shell script named x.sh, and inside nano i typed /challenge/pwn and /challenge/college, on two different lines. Then i connected the output of the shell script using bash (bash x.sh) to the input of /challenge/solve using pipe (|) operator and got the flag.  

```
hacker@chaining~redirecting-script-output:~$ nano x.sh
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{MrvTzQumZqn0s3DqJUuFAB93jbY.QX4ETO0wiN3kjNzEzW}
```

## What I learnt
I learned that for the shell, the shell script is just like another command. So we can redirect its input and output with various methods we learned in previus modules like >,|.2>,<,>>,etc.  

## References
pwn.college instructions.

# 6. Executable shell scripts: 
### In this challenge, they told us to create a script that will invoke the /challenge/solve, make it executable, and then run it without invoking bash to get the flag. 

## My solve
**pwn.college{AaZm8-s_G5BK3WWAVAIW7a6wLqC.QX0cjM1wiN3kjNzEzW}**

I used nano command to create a shell script named x.sh, and inside nano i typed /challenge/solve. I then changed the permissions of the file to allow the user (that is me) to execute the file using chmod u+x. Then i executed the x.sh file to get the flag. 

```
hacker@chaining~redirecting-script-output:~$ nano x.sh
hacker@chaining~executable-shell-scripts:~$ ./x.sh
bash: ./x.sh: Permission denied
hacker@chaining~executable-shell-scripts:~$ ls -l ./x.sh
-rw-r--r-- 1 hacker hacker 16 Oct 10 19:45 ./x.sh
hacker@chaining~executable-shell-scripts:~$ chmod u+x ./x.sh
hacker@chaining~executable-shell-scripts:~$ ./x.sh
Congratulations on your shell script execution! Your flag:
pwn.college{AaZm8-s_G5BK3WWAVAIW7a6wLqC.QX0cjM1wiN3kjNzEzW}
```

## What I learnt
I learned that we can directly execute the shell script files, if we have executable (x) permissions for that.   

## References
pwn.college instructions.

# 7. Understanding Shebangs:  
### In this challenge, they asked us to create a script at /home/hacker/solve.sh that has a proper shebang and outputs "hack the planet". We had to make it executable, then run /challenge/run to verify your script works correctly to get the flag. 

## My solve
**pwn.college{w_UZedPlPtcR2AtY0dGypBF3woi.0VOzMDOxwiN3kjNzEzW}**

I used nano command to create a shell script named solve.sh. Inside the shell script, i kept the shebang as #!/bin/bash as its a bash script and typed echo "hack the planet". I then made it executable using chmod command and then ran /challenge/run to get the flag. 

```
hacker@chaining~redirecting-script-output:~$ nano solve.sh
hacker@chaining~understanding-shebangs:~$ ls -l ./solve.sh
-rw-r--r-- 1 hacker hacker 36 Oct 10 20:06 ./solve.sh
hacker@chaining~understanding-shebangs:~$ chmod u+x ./solve.sh
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{w_UZedPlPtcR2AtY0dGypBF3woi.0VOzMDOxwiN3kjNzEzW}
```

## What I learnt
I learned about shebangs. They start with #!. There are a bunch of different types of programs, but if the program file starts with the characters #!, Linux treats the file as an interpreted program, and the contents of the rest of the line as the path to the interpreter. It then invokes the interpreter with the path to the program file as its only argument. The shebang line must be the VERY FIRST line of the file - no blank lines or spaces before it. Common shebangs:

#!/bin/bash for bash scripts

#!/usr/bin/python3 for Python scripts

#!/bin/sh for POSIX shell scripts, this is a more primitive predecessor to bash with fewer features, but more compatibility to non-Linux systems.

## References
pwn.college instructions.

# 7. Scripting with arguments: 
### In this challenge, they told us to make a script such that it takes 2 arguments and outputs them in reverse order. After the script is ready, they told us to run /challenge/run to get the flag. 

## My solve
**pwn.college{Ijonx-D4xKlBzQMvgzwbGHVm3gP.0VNzMDOxwiN3kjNzEzW}**

I used nano command to create a shell script named solve.sh, and inside nano i typed echo "$2 $1". After that i invoked /challenge/run to get the flag. 

```
hacker@chaining~redirecting-script-output:~$ nano solve.sh
hacker@chaining~scripting-with-arguments:~$ bash solve.sh hi hello
hello hi
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{Ijonx-D4xKlBzQMvgzwbGHVm3gP.0VNzMDOxwiN3kjNzEzW}
```

## What I learnt
I learned that scripts can accept arguments. For example: bash script.sh argument1 argument2, $1 contains argument1 and $2 contains argument2, and so on.   

## References
pwn.college instructions.

# 8. Scripting with conditionals: 
### In this challenge, they told us to make a script such that it takes 1 argument, and if the argument is pwn, then it outputs college, and for any other input it outputs nothing. Once the script is done they asked us to run /challenge/run to get the flag.

## My solve
**pwn.college{AOnb-RxhrmRfTrzsBbyRJR8coQn.0lNzMDOxwiN3kjNzEzW}**

I used nano command to create a shell script named solve.sh, and inside nano i typed the script for outputting college if the argument is pwn. Then i ran /challenge/run to get the flag.  

```
hacker@chaining~redirecting-script-output:~$ nano solve.sh
hacker@chaining~scripting-with-conditionals:~$ bash solve.ch pwn
bash: solve.ch: No such file or directory
hacker@chaining~scripting-with-conditionals:~$ bash ./solve.sh pwn
college
hacker@chaining~scripting-with-conditionals:~$ bash ./solve.sh ssh
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{AOnb-RxhrmRfTrzsBbyRJR8coQn.0lNzMDOxwiN3kjNzEzW}

nano:
#!/bin/bash

if [ "$1" == "pwn" ]
then 
    echo "college" 
fi
```

## What I learnt
I learned that we can also use conditional statements with arguments in the script. We should be careful with the syntax here as its a little weird. 

## References
pwn.college instructions.
