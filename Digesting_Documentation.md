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

### In this challenge, it was similar to the previous challenge, where we had to read the manual page of 'challenge' to find the correct argument to get the flag. But over here we have to search in the manual as the manual was very big. 

**Flag:** `pwn.college{An2Zf4yXJZ3UgR7g91wS_Td9itF.QX1EDO0wiN3kjNzEzW}`

I first opened the manual page of challenge with the 'man' command, then i searched for all the 'flag' words using '/' and '?' and 'n' and 'N' to navigate around, until i found the correct argument to use to get the flag.  

```
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --qp
Initializing...
Correct usage! Your flag: pwn.college{An2Zf4yXJZ3UgR7g91wS_Td9itF.QX1EDO0wiN3kjNzEzW}
```

## What I learned

I learned how to search for keywords inside manual pages (manpages) in linux. We have to use '/' to search or '?' to search backwards. After searching, we can click 'n' to go to the next result or 'N' to go to the previous result. You can scroll man pages with the arrow keys.

## References

The reference used was the challenge statement and docummentation given in pwn.college. The inbuilt manpages was also used.

# 5. Searching for manuals: 

### In this challenge, it hid the  manpage for the challenge by randomizing its name. It asked us to search the manpage database to find the hidden challenge man page. The following hints were given: 1)  man man teaches you advanced usage of the man command itself, and you must use this knowledge to figure out how to search for the hidden manpage that will tell you how to use /challenge/challenge. 2) though the manpage is randomly named, you still actually use /challenge/challenge to get the flag.

**Flag:** `pwn.college{w-M9KHBuISEwpNbb0JVWC1L3d4F.QX2EDO0wiN3kjNzEzW}`

I first went into the manpage of 'man' command, and searched for the keyword 'search', as we had to find a argument to search the database of all manpages. I then looked around and saw the '--wildcard' argument, which searches all the manpages names and description for a keyword. I used this argument used the keyword flag to search all the manpages for flag. It then opened the manpage for '/challenge/challenge' program and inside that manpage was the argument when used with the program, gave the flag. The argument was -wuwpbb 901.  I used this command with the argument to get the flag.  

```
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$ man --wildcard flag
hacker@man~searching-for-manuals:~$ /challenge/challenge --wuwpbb 901
Correct usage! Your flag: pwn.college{w-M9KHBuISEwpNbb0JVWC1L3d4F.QX2EDO0wiN3kjNzEzW}
```

## What I learned

I learned that there is a manpage for the 'man' command also. I also learned that there is a searchable database containing all the manpages, and we can search many different things in that like keywords in both program/files names or descriptions. We can always use the manpages and the searching tool inside the manpages for reference. 

## References

The reference used was the challenge statement and docummentation given in pwn.college. The inbuilt manpages was also used.

# 6. Helpful programs: 

### This program told us to use the '--help' argument with /challenge/challenge program to get hints on how to get the flag. 

**Flag:** `pwn.college{8NJ36pejhTpEFDcA90xVM3NG_Ei.QX3IDO0wiN3kjNzEzW}`

I first ran the program with '--help' argument as they told, which gave a way on how we can use the command. It told at the last that we need to get a value with the '-p' argument to keep it along with the '-g' argument to get the flag. So i used the '-p' argument to get the value and i used '-g' argument along with the value to get the flag. I first accidently copy pasted the entire argument from the help page instead of replacing the placeholder (GIVE_THE_FLAG) with the value. 

```
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge --print-value
The secret value is: 836
hacker@man~helpful-programs:~$ /challenge/challenge --give-the-flag GIVE_THE_FLAG
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]
a challenge to make you ask for help: error: argument -g/--give-the-flag: invalid int value: 'GIVE_THE_FLAG'
hacker@man~helpful-programs:~$ /challenge/challenge --give-the-flag 836
Correct usage! Your flag: pwn.college{8NJ36pejhTpEFDcA90xVM3NG_Ei.QX3IDO0wiN3kjNzEzW}
```

## What I learned

I learned that not all commands have a man page, some don't. However, we can use the '--help- or sometimes '-h' argument along with the command to know how to use the command. 

## References

The reference used was the challenge statement and docummentation given in pwn.college. The inbuilt help page with the '--help' argument was also used.

# 7. Help for Builtins: 

### In this challenge, the challenge command is a shell builtin, rather than a program. We need to look at its help to find the secret value and get the flag. 

**Flag:** `pwn.college{IBSSJTi9DYLWeDgDNoUEo2r3ptJ.QX0ETO0wiN3kjNzEzW}`

I used the 'help' to lookup help for builtins. I first used 'challenge help' but this is wrong, for builtins we need to use 'help challenge', in place of challenge any builtin can be there. In that help page, the secret value and the argument to get the flag was given. I then ran the challenge command with the argument and the secret value given in help to get the flag.  

```
hacker@man~help-for-builtins:~$ challenge help
Incorrect usage! Please read the help page for the challenge builtin!
hacker@man~help-for-builtins:~$ challenge help
Incorrect usage! Please read the help page for the challenge builtin!
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "IBSSJTi9".
hacker@man~help-for-builtins:~$ challenge --secret IBSSJTi9
Correct! Here is your flag!
pwn.college{IBSSJTi9DYLWeDgDNoUEo2r3ptJ.QX0ETO0wiN3kjNzEzW}
```

## What I learned

i first learned about builtins, which are commands that are inbuilt into the shell itself, instead of being programs with man pages and help options. Builtins are invoked just like commands, but the shell handles them internally instead of launching other programs. We can get a list of all shell builtins with the 'help' builtin. We can get help on a specific builtin by passing it to the help builtin, like 'help cd' (in place of cd you can put any builtin, and yes cd is a builtin). 

## References

The reference used was the challenge statement and docummentation given in pwn.college. The help command for inbuilts was also used. 
