# 1. Printing variables: 

### In this challenge, they told that The /challenge/run program will not, and cannot, give you the flag, but the flag has been put into the variable called "FLAG". We need to have our shell print out the FLAG variable.

**Flag:** `pwn.college{QuSjw0W7Ob5c261LhhKtWEjpKuY.QX3UTN0wiN3kjNzEzW}`

I printed the variable "FLAG" by using the echo command and using the "$" sign infront of the variable name in the argument. 

```
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{QuSjw0W7Ob5c261LhhKtWEjpKuY.QX3UTN0wiN3kjNzEzW}
```

## What I learned

I learned how we can print variables. One way to do it is by using echo command and putting a dollar sign ($) infront of the variable name in the argument. For example: echo $VARIABLENAME.

## References

The references i used were the challenge ctatements in pwn.college and https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html.

# 2. Setting variables: 

### In this challenge, they asked us to set the PWN variable to the value COLLEGE to get the flag. 

**Flag:** `pwn.college{8YRAmAbwJc0RCm6uykZ-6zB6dtc.QX5UTN0wiN3kjNzEzW}`

I set the PWN variable to the value COLLEGE by using equal to (=) symbol (PWN=COLLEGE), then i got the flag. 

```
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{8YRAmAbwJc0RCm6uykZ-6zB6dtc.QX5UTN0wiN3kjNzEzW}
```

## What I learned

I learned how we can write values to variables. We can do it with the equal to (=) symbol. For example: HI=13. We should not keep  spaces around the =. If we put spaces (e.g., VAR = 1337), the shell won't 
recognize a variable assignment and will, instead, try to run the VAR command. Also, both the names and values of variables are case-sensitive (HI!=hi).I also learned that the $ is only prepended to access 
variables, so we dont use it while assigning values to variables. In shell terms, this prepending of $ triggers what is called variable expansion.

## References

The references i used were the challenge ctatements in pwn.college and https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html.

# 3. Multi-word variables:: 

### In this challenge, they asked us to set the PWN variable to the value "COLLEGE YEAH" to get the flag.  

**Flag:** `pwn.college{oCRG8syQ0unOx7ls64IllURC3mz.QXwYTN0wiN3kjNzEzW}`

I set the PWN variable to the value COLLEGE YEAH by using equal to symbol (=) and also using double quotes to keep "COLLEGE YEAH", since space is there. 

```
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{oCRG8syQ0unOx7ls64IllURC3mz.QXwYTN0wiN3kjNzEzW}
```

## What I learned

I learned how we can assign values with spaces to variables. We have to use double quotes for the value with spaces. 

## References

The references i used were the challenge ctatements in pwn.college and https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html.

# 4. Exporting Variables
### In this challenge, they asked us to run  /challenge/run with the PWN variable exported and set to the value COLLEGE, and the COLLEGE variable set to the value PWN but not exported.

## My solve
**pwn.college{gdSbS6iyAF0Tpgh6UaOxNNlnQXh.QXyYTN0wiN3kjNzEzW}**

To solve this challenge, I assigned the value COLLEGE to the variable PWN and exported it. I then assigned the value PWN to the variable COLLEGE without exporting it. I then ran /challenge/run to retrive the flag.

```
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{gdSbS6iyAF0Tpgh6UaOxNNlnQXh.QXyYTN0wiN3kjNzEzW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```

## What I learnt
I learnt how to export values assigned to variable if you want them to remain assigned using "export". Generally, without exporting, the value assigned to the variables do not carry forward to the child programs 
within. On exporting them, they do.

## References
https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html and the pwn.college instructions.

# 5. Printing exported variables
### In this challenge, they asked us to use the env command, which will print out every exported variable set in our shell, and look through that output to find the FLAG variable. 

## My solve
**pwn.college{wmWoD0mhjmrC61w394MNUBZx3b2.QX4UTN0wiN3kjNzEzW}**

I used the env command, which listed out all the exported variables in the shell. I looked for the FLAG variable for the flag and found it.  

```
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=797543930c277a09c9f95f3e6ae940ddaf53b6aa74a0459161160465109d536f
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{wmWoD0mhjmrC61w394MNUBZx3b2.QX4UTN0wiN3kjNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
_=/run/dojo/bin/env
```

## What I learnt

I learned about the "env" command, which is another way to access variables. It will print out all exported variables in the shell and if we put the name of the variable with $ sign, then it will print the value 
of that variable. For example: env $FLAG. 

## References
https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html and the pwn.college instructions.

# 6. Storing Command Output
### In this challenge, they asked us to read the output of the /challenge/run command directly into a variable called PWN, then read PWN to get the flag. 

## My solve
**pwn.college{0dVlLKRqM0UyH3X5Et7ZnTZPUAk.QX1cDN1wiN3kjNzEzW}**

I first assigned the output of /challenge/run to the PWN variable using () and $ signs, then i read the variable using echo command to get the flag. 

```
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{0dVlLKRqM0UyH3X5Et7ZnTZPUAk.QX1cDN1wiN3kjNzEzW}
```

## What I learnt
I learned about command substitution, which is basically assigning the output of a command to a variable. We can do it by using $ and (). For example: variable=$(COMMAND). 

## References
https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html and the pwn.college instructions.


# 7. Reading Input
### In this challenge, they asked us to use the read command to set the PWN variable to the value COLLEGE to get the flag. 

## My solve
**pwn.college{QU8F8Hu85zuHDpy-qTCMtidevnz.QX4cTN0wiN3kjNzEzW}**

I used the read command to take input from the user and stored it in PWN variable. I also used the -p command, which is used for giving a prompt. I used "Input: " as the prompt. I then typed COLLEGE as the input 
to get the flag. 

```
hacker@variables~reading-input:~$ read -p "input: " PWN
input: COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{QU8F8Hu85zuHDpy-qTCMtidevnz.QX4cTN0wiN3kjNzEzW}
```

## What I learnt
I learned about the read command, which is used to read inputs from the user. -p argument can be used to give prompt to the user, for making it easier for user. We can also the name of a variable or file as 
another argument, to make the input entered by the user stored in that variable/file. For example: read -p "Input: " hi, will give the prompt "Input: ", and it will store the input entered by the user in hi.

## References
https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html and the pwn.college instructions.


# 8. Reading Files
### In this challenge, they asked us to use read to read /challenge/read_me into the PWN environment variable to get the flag. They also told that the /challenge/read_me will keep changing, so you'll need to read it right into the PWN variable with one command.

## My solve
**pwn.college{0P54iQlXKrmixs_lYs6Nk5icbjo.QXwIDO0wiN3kjNzEzW}**

I first redirected /challenge/read_me output to the standard input of read, so it reads the output into PWN. 

```
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{0P54iQlXKrmixs_lYs6Nk5icbjo.QXwIDO0wiN3kjNzEzW}
```

## What I learnt
I have learnt how to read files directly into a variable through the read command.

## References
https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html and the pwn.college instructions.
