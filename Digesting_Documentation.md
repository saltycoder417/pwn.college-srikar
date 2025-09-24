# 1. Learning from documentation: 

### In this challenge, a program was given to run with a specific argument to get the flag. The program was '/challenge/challenge' and the argument we have to use is '--giveflag'. The argument was given in the documentation of the program.

**Flag:** `pwn.college{MakBG45ZOH73DdJ0CNvpohX8Gvg.QX0ITO0wiN3kjNzEzW}`

I invoked the given program along with the argument they gave in the terminal to get the flag.

```
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{MakBG45ZOH73DdJ0CNvpohX8Gvg.QX0ITO0wiN3kjNzEzW}
```

## What I learned

I learned how the correct usage of programs depends, in a large part, on the proper specification of arguments to them. I also learned one of the need of a documentation of a program is to figure out which 
argument to use on the command line. One of the main needs of a documentation is to figure out how to use programs correctly.

## References

The reference used was the challenge statement and docummentation given in pwn.college. 

# 2. Learning complex usage: 

### In this challenge, a documentation for '/challenge/challenge' program was given. This documentation provided that if we run the program, it will print arbitrary files to the terminal, when we give it the '--printfile argument'. It also told that we have to give the path of the file as the argument to '--printfile'. 

**Flag:** `pwn.college{k8yw9BWY5BO_dZJpl4N8bYbdM-m.QX1ITO0wiN3kjNzEzW}`

I invoked the '/challenge/challenge' program with the '--printfile' argumant, along with the path to the flag (/flag) as the argument to '--printfile'. This entire command then printed the flag file and i got the flag.

```
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{k8yw9BWY5BO_dZJpl4N8bYbdM-m.QX1ITO0wiN3kjNzEzW}
```

## What I learned

I learned that some commands take arguments to their arguments. For example, 'find' has a '-name' argument, and the '-name' argument itself takes an argument specifying the name to search for.

## References

The reference used was the challenge statement and docummentation given in pwn.college. 

# 3. Reading manuals: 

### In this challenge, there was a secret option that, when you use it, will cause the challenge to print the flag. The 'man' command was introduced and we have to go through the manpage of 'challenge' to get the flag.

**Flag:** ` pwn.college{8unln2rJJW1ed04bBus5VV8ws03.QX0EDO0wiN3kjNzEzW}`

I first opened the manual page of 'challenge' by using the 'man' command with 'challenge' as the argument. In the manual, it was given that '/challenge/challenge' program prints the flag if the correct argument --unlnre 821 is given. So i ran the program with the argument they gave to print the flag.  

```
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ /challenge/challenge --unlnre 821
Correct usage! Your flag: pwn.college{8unln2rJJW1ed04bBus5VV8ws03.QX0EDO0wiN3kjNzEzW}
```

## What I learned

I learned about the man command. It will display (if available) the manual of the command you pass as an argument. For example: man cd. Manpages are stored in a centralized database and that database lives in the /usr/share/man directory, but we dont need to interact with it directly, we can just use the man command. 

## References

The reference used was the challenge statement and docummentation given in pwn.college. 

# 4. Searching manuals: 

### Put challenge description here

**Flag:** `pwn.college{helloworld}`

explain your solve and how you got to it, explain any incorrect tangents you went on while solving.

to put code snippets, put three backticks and for images and all other stuff you wish to put here, refer to the documentation given to you.

don't style it too much, your solve should be readable and understandable by you so that when you have doubts, you refer to your own writeups, instead of gpt.

```
#!/bin/bash

example triple ticks for bash

pwn.college{helloworld}
```

## What I learned

explain what you learned

## References

Add an references or videos you used while solving the challenge.

# 5. 

### Put challenge description here

**Flag:** `pwn.college{helloworld}`

explain your solve and how you got to it, explain any incorrect tangents you went on while solving.

to put code snippets, put three backticks and for images and all other stuff you wish to put here, refer to the documentation given to you.

don't style it too much, your solve should be readable and understandable by you so that when you have doubts, you refer to your own writeups, instead of gpt.

```
#!/bin/bash

example triple ticks for bash

pwn.college{helloworld}
```

## What I learned

explain what you learned

## References

Add an references or videos you used while solving the challenge.

# 6. 

### Put challenge description here

**Flag:** `pwn.college{helloworld}`

explain your solve and how you got to it, explain any incorrect tangents you went on while solving.

to put code snippets, put three backticks and for images and all other stuff you wish to put here, refer to the documentation given to you.

don't style it too much, your solve should be readable and understandable by you so that when you have doubts, you refer to your own writeups, instead of gpt.

```
#!/bin/bash

example triple ticks for bash

pwn.college{helloworld}
```

## What I learned

explain what you learned

## References

Add an references or videos you used while solving the challenge.

# 7. 

### Put challenge description here

**Flag:** `pwn.college{helloworld}`

explain your solve and how you got to it, explain any incorrect tangents you went on while solving.

to put code snippets, put three backticks and for images and all other stuff you wish to put here, refer to the documentation given to you.

don't style it too much, your solve should be readable and understandable by you so that when you have doubts, you refer to your own writeups, instead of gpt.

```
#!/bin/bash

example triple ticks for bash

pwn.college{helloworld}
```

## What I learned

explain what you learned

## References

Add an references or videos you used while solving the challenge.
