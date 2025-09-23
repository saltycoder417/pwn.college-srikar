# 1.The root: 

### This challenge first explained about the basic linux filesystem and about the root. We had to invoke the pwn program in the root directory to get the flag. 

**Flag:** `pwn.college{E2IRr10yhH3J6qZiFnHeTXggyqm.QX4cTO0wiN3kjNzEzW}`

The challenge told that the flag was kept inside the pwn program in root directory and we had to invoke this program. To invoke a program, we have to provide its path on the command line. So i provided the path of
the program "/pwn" program and got the flag. 

```
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{E2IRr10yhH3J6qZiFnHeTXggyqm.QX4cTO0wiN3kjNzEzW}
```

## What I learned

I learnt the basics about how the linux file system and about the root directory (written by /), which contains all the other directories. I also learnt what a path is, how to invoke it and also about absolute paths,
which are paths that start with the root directory.

## References

The references used were the problem statement itself in pwn.college and also the video provided above the challenges. 
video link: https://www.youtube.com/watch?v=b67Jq6IZ3U8&list=PL-ymxv0nOtqqRAz1x90vxNbhmSkeYxHVC&t=1127s

# 2.Program and absolute paths: 

### This challenge was similar to the previous challenge, but this time the flag was in run program which was in the challenge directory which was again in the root directory.

**Flag:** `pwn.college{EzfU5soT_WJwekdM4Sk5C277Fn_.QX1QTN0wiN3kjNzEzW}`

As mentioned above, the flag was kept in the run program. So i typed the absolute path of run program and got the flag.

```
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{EzfU5soT_WJwekdM4Sk5C277Fn_.QX1QTN0wiN3kjNzEzW}
```

## What I learned

I learnt how linux uses nested directories for better organisation and how we should invoke the absolute path of any file, program or directory. 

## References

The references used were the problem statement itself in pwn.college and also the video provided above the challenges. 
video link: https://www.youtube.com/watch?v=b67Jq6IZ3U8&list=PL-ymxv0nOtqqRAz1x90vxNbhmSkeYxHVC&t=1127s

# 3. position thy self: 

### In this challenge, it was given to execute the run program after changing the cwd(current working directory).

**Flag:** `pwn.college{U7_hnAEu_EGoA1az8mYFsG1J8On.QX2QTN0wiN3kjNzEzW}`

I first typed the absolute path of run to execute the program. It then then me the working directory i have to be in to get the flag. I used the cd command to change the working directory and then ran the program
again to get the flag.

```
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /proc/131/fd directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /proc/131/fd
hacker@paths~position-thy-self:/proc/131/fd$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{U7_hnAEu_EGoA1az8mYFsG1J8On.QX2QTN0wiN3kjNzEzW}
```

## What I learned

I leanrt about what the current working directory is: it is basically where (which directory) the process currently is in. I also learnt how we can use the cd command to change the current working directory.
Also that '~' in the prompt shows the current path your shell is at.

## References

The references used were the problem statement itself in pwn.college and also the video provided above the challenges. 
video link: https://www.youtube.com/watch?v=b67Jq6IZ3U8&list=PL-ymxv0nOtqqRAz1x90vxNbhmSkeYxHVC&t=1127s

# 4. Position elsewhere: 

### In this challenge, it was given to execute the run program after changing the cwd(current working directory). Similar to the previous challenge. 

**Flag:** `pwn.college{w6LFkM0Uo3jH9VQ4D2zOPwsmn6T.QX3QTN0wiN3kjNzEzW}`

I first typed the absolute path of run to execute the program. It then then me the working directory i have to be in to get the flag. I used the cd command to change the working directory and then ran the program
again to get the flag.

```
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /proc/132 directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /proc/132
hacker@paths~position-elsewhere:/proc/132$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{w6LFkM0Uo3jH9VQ4D2zOPwsmn6T.QX3QTN0wiN3kjNzEzW}
```

## References

The references used were the problem statement itself in pwn.college and also the video provided above the challenges. 
video link: https://www.youtube.com/watch?v=b67Jq6IZ3U8&list=PL-ymxv0nOtqqRAz1x90vxNbhmSkeYxHVC&t=1127s

# 5. Position yet elsewhere: 

### In this challenge, it was given to execute the run program after changing the cwd(current working directory). Similar to the previous challenge. 

**Flag:** `pwn.college{k7W8Zo6owE_VeDOhTFu5rpuV4Ts.QX4QTN0wiN3kjNzEzW}`

I first typed the absolute path of run to execute the program. It then then me the working directory i have to be in to get the flag. I used the cd command to change the working directory and then ran the program
again to get the flag.

```
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/zoneinfo/posix/Asia directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /usr/share/zoneinfo/posix/Asia
hacker@paths~position-yet-elsewhere:/usr/share/zoneinfo/posix/Asia$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{k7W8Zo6owE_VeDOhTFu5rpuV4Ts.QX4QTN0wiN3kjNzEzW}
```

## References

The references used were the problem statement itself in pwn.college and also the video provided above the challenges. 
video link: https://www.youtube.com/watch?v=b67Jq6IZ3U8&list=PL-ymxv0nOtqqRAz1x90vxNbhmSkeYxHVC&t=1127s

# 6. Implicit relative paths, from /: 

### In this challenge, it was given to run '/challenge/run' using a relative path while having a current working directory of '/'.

**Flag:** `pwn.college{glNhpW_t4BZyneEu_TIkW-0QTq1.QX5QTN0wiN3kjNzEzW}`

I first changed my cwd to the root as they told in the problem. Then i ran 'challenge/run', which is a relative path for the 'run' program where the flag was prsent. 

```
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{glNhpW_t4BZyneEu_TIkW-0QTq1.QX5QTN0wiN3kjNzEzW}
```

## What I learned

I learnt about relative paths: which are paths that are relative to the cwd. They don't start with the root. It is interpreted relative to your cwd. 

## References

The references used were the problem statement itself in pwn.college and also the video provided above the challenges. 
video link: https://www.youtube.com/watch?v=b67Jq6IZ3U8&list=PL-ymxv0nOtqqRAz1x90vxNbhmSkeYxHVC&t=1127s

# 7. Explicit relative paths, from /: 

### In this challenge, it was given to use '.' in the relative paths to get the flag. 

**Flag:** `pwn.college{g0ruho9b5o3x9eV1zA2AaoCkxl-.QXwUTN0wiN3kjNzEzW}`

I first changed my cwd to the root, then i typed the relative path of the run program using '.' to get the flag. 

```
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{g0ruho9b5o3x9eV1zA2AaoCkxl-.QXwUTN0wiN3kjNzEzW}
```

## What I learned

I learnt about the implicit entries we can use for reference: '.' and '..'. '.' refers to the same directory as the cwd, and '..' refers to the parent directory of the cwd. 

## References

The references used were the problem statement itself in pwn.college and also the video provided above the challenges. 
video link: https://www.youtube.com/watch?v=b67Jq6IZ3U8&list=PL-ymxv0nOtqqRAz1x90vxNbhmSkeYxHVC&t=1127s

# 8. Implicit relative path: 

### In this challenge, it was given to run the program explicitly using '.' from the challenge directory.

**Flag:** `pwn.college{EcBmX7jdZTosB7rWAQhCNNyj3x7.QXxUTN0wiN3kjNzEzW}`

I first changed my cwd to challenge directory as given in the problem. Then i gave the explicit relative path of run program to get the flag. 

```
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{EcBmX7jdZTosB7rWAQhCNNyj3x7.QXxUTN0wiN3kjNzEzW}
```

## What I learned

I learnt what a "naked" path is and what how to explictly run relative paths. We had to explictly run it because if we type 'run' directly, Linux will not invoke '/challenge/run' to avoid accidently executing 
programs in your current directory that may have the same names as core system utilities if we ran it through a "naked path".

## References

The references used were the problem statement itself in pwn.college and also the video provided above the challenges. 
video link: https://www.youtube.com/watch?v=b67Jq6IZ3U8&list=PL-ymxv0nOtqqRAz1x90vxNbhmSkeYxHVC&t=1127s

# 9. home sweet home: 

### In this challenge, it was given that '/challenge/run' command will copy the flag to a file which we have to specify in the argument with 3 conditions. Your argument must be an absolute path, The path must be inside your home directory, and Before expansion, your argument must be three characters or less.

**Flag:** `pwn.college{4rV9fJ70M9r38lzYNA2NGRXKBMG.QXzMDO0wiN3kjNzEzW}`

I first wrote the command they gave for copying a file and i wrote the argument as some directory 'i' inside the home directory(~). It then read the file to me which gave the flag. 


```
hacker@paths~home-sweet-home:~$ /challenge/run ~/i
Writing the file to /home/hacker/i!
... and reading it back to you:
pwn.college{4rV9fJ70M9r38lzYNA2NGRXKBMG.QXzMDO0wiN3kjNzEzW}
```

## What I learned

The main thing i learnt here is about the home directory, which is where most of the user's personal files are stored. The shell also starts the cwd with the home directory. The symbol (~) which comes in many 
prompts is nothing but the shortform for the user directory (in the case of pwn.college it is /home/hacker). This shortform is provided because most of the time will generally be spent in the home directory.
(~) is an absolute path and only the leading is expanded. This means, for example, that the (~/~) will be expanded to '/home/hacker/~' rather than '/home/hacker/home/hacker'.
## References

The references used were the problem statement itself in pwn.college and also the video provided above the challenges. 
video link: https://www.youtube.com/watch?v=b67Jq6IZ3U8&list=PL-ymxv0nOtqqRAz1x90vxNbhmSkeYxHVC&t=1127s
