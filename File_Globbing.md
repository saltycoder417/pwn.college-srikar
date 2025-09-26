# 1. Matching with *: 

### In this challenge, it was given to change your directory to '/challenge', but use globbing to keep the argument you pass to cd to at most four characters. After that it told to run '/challenge/run' to get the flag.

**Flag:** `pwn.college{YldJl_3dPGSdHeXtjc9cDhz7qRa.QXxIDO0wiN3kjNzEzW}`

I changed my cwd to '/challenge' and kept it within 4 characters by using '*' glob. After the cwd changed, i ran the program to get the flag. 

```
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{YldJl_3dPGSdHeXtjc9cDhz7qRa.QXxIDO0wiN3kjNzEzW}
```

## What I learned

I first learned about globbing. Globbing lets you reference files without typing out their full paths. Before executing commands that you enter, the shell first performs expansions on them, and one of these 
expansions is globbing. In this challenge, i learned about the "star" glob, When it encounters a "star" character in any argument, the shell will treat it as a wildcard and try to replace that argument with any files 
that match the pattern. It can match multiple files or single files also if only 1 file is there with that pattern. When zero files are matched,the shell leaves the glob unchanged. The "star" matches any part of the 
filename except for "/" or a leading ".".

## References

The reference i used is the challenge statement in pwn.college. 


# 2. Matching with ?: 

### In this challenge, it was given to change your directory to '/challenge' from home directory using the '?' glob instead of c and l. After that it was given to run '/challenge/run' to get the flag. 

**Flag:** `pwn.college{g9J0H8qIkWhoeTVSVjqFuOfUguV.QXyIDO0wiN3kjNzEzW}`

I first used the cd command along with '/?ha??enge' command, as they told to replace c and l with glob. Then i ran the program to get the flag.

```
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{g9J0H8qIkWhoeTVSVjqFuOfUguV.QXyIDO0wiN3kjNzEzW}
```

## What I learned

I learned about the '?' glob. It is similar to the star glob but it only matches one character. The shell basically treats it like a single character wildcard. 

## References

The reference i used is the challenge statement in pwn.college. 

# 3. Matching with []: 

### In this challenge, it asked us to first Change our working directory to /challenge/files and run /challenge/run with a single argument that bracket-globs into file_b, file_a, file_s, and file_h.

**Flag:** `pwn.college{wYCStS2sCM-0m6bYMvj6SGsXpGa.QXzIDO0wiN3kjNzEzW}`

I first used the cd command to change the cwd to /challenge/files. Then i used the square bracket glob with letters b,a,s,h inside (like bash) as the argument for /challenge/run to get the flag. I first accidently wrote files instead of file in the argument. 

```
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run files_[bash]
Your expansion did not expand to the requested files (file_a, file_b, file_h,
and file_s). Instead, it expanded to:
files_[bash]
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{wYCStS2sCM-0m6bYMvj6SGsXpGa.QXzIDO0wiN3kjNzEzW}
```

## What I learned

I learned about the square bracket glob. The square brackets are, essentially, a limited form of "?", in that instead of matching any character, square bracket is a wildcard for some subset of potential characters, specified within the brackets. For example, "[pwn]" will match the character p, w, or n.

## References

The reference i used is the challenge statement in pwn.college. 

# 4. Matching paths with []: 

### This challenge was similar to the previous challenge, Just that we have to start from our home directory and we have to run /challenge/run with a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h files.

**Flag:** `pwn.college{Y3Oh8tHUs67T2r752f434WCxezG.QX0IDO0wiN3kjNzEzW}`

I ran the /challenge/run program with the absolute path of all the files globbed into a square bracket.

```
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{Y3Oh8tHUs67T2r752f434WCxezG.QX0IDO0wiN3kjNzEzW}
```

## What I learned

I learned that we can also expand entire paths with globbed arguments. I also learned that globbing happens on a path basis. 

## References

The reference i used is the challenge statement in pwn.college.

# 5. Multiple globs: 

### In this challenge/ it asked us to change the working directory to /challenge/files, then  run /challenge/run, providing a single argument: a short (3 characters or less) globbed word with two * globs in it that covers every word that contains the letter p.

**Flag:** `pwn.college{oQXejiaBKHfXxxDpvqfZBQYTRKe.0lM3kjNxwiN3kjNzEzW}`

I first used the cd command to change the cwd to /challenge/files. Then i used the /challenge/run with two star globs and p in between as arguments to get the flag. 

```
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ ls
amazing      delightful   great       jovial    magical     pwning   splendid   victorious  youthful
beautiful    educational  happy       kind      nice        queenly  thrilling  wonderful   zesty
challenging  fantastic    incredible  laughing  optimistic  radiant  uplifting  xenial
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{oQXejiaBKHfXxxDpvqfZBQYTRKe.0lM3kjNxwiN3kjNzEzW}
```

## What I learned

I learned that we can use multiple globs at a time that too in a single word also. 

## References

The reference i used is the challenge statement in pwn.college.

# 6. Mixing globs: 

### In this challenge, they asked us to cd to /challenge/files, then using the globbing we learned till now, we had to write a single, short (6 characters or less) glob that (when passed as an argument to /challenge/run) will match the files "challenging", "educational", and "pwning".

**Flag:** `pwn.college{0ODCxuwvxxJXR1er-em3Ml05aMK.QX1IDO0wiN3kjNzEzW}`

I first used cd command to change the cwd to /challenge/files, then i ran the program with /challenge/run with c,e,p inside square brackets and 1 star as globs as the argument, this argument was exactly 6 characters, and i got the flag. This argument will match all the files that start with either c,p or e. 

```

hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{0ODCxuwvxxJXR1er-em3Ml05aMK.QX1IDO0wiN3kjNzEzW}
```

## What I learned

I learned that we can use different types of globs into the same argument and the shell will expand it. 

## References

The reference i used is the challenge statement in pwn.college.

# 7. Exclusionary globbing: 

### In this challenge, they asked us to go to /challenge/files and then run /challenge/run with all files that don't start with p, w, or n as argument. 

**Flag:** `pwn.college{MO5vHewAoiz6ie6wFGVlVktVOka.QX2IDO0wiN3kjNzEzW}`

As they gave, i first changed the cwd to /challenge/files using cd command. Then i ran the program along with using the square brackets glob with (!pwn) inside to exclude those files which are starting with p,w, or n (exclusionary globbing), and i kept the star glob to include all files after that. I first didnt keep the star globe, then realised that without it, no file is mentioned, as in there is no expansion. 

```
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]
Your expansion did not expand to the requested files (amazing beautiful
challenging delightful educational fantastic great happy incredible jovial kind
laughing magical optimistic queenly radiant splendid thrilling uplifting
victorious xenial youthful zesty).
Instead, it expanded to:
[^pwn]
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]
Your expansion did not expand to the requested files (amazing beautiful
challenging delightful educational fantastic great happy incredible jovial kind
laughing magical optimistic queenly radiant splendid thrilling uplifting
victorious xenial youthful zesty).
Instead, it expanded to:
[!pwn]
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{MO5vHewAoiz6ie6wFGVlVktVOka.QX2IDO0wiN3kjNzEzW}
```

## What I learned

I learned that we can also exclude some characters while globbing using square bracket glob and starting either ! or ^ inside the bracket and then keeping the letters we want to exclude. 

## References

The reference i used is the challenge statement in pwn.college, and also the error given in the terminal. 

# 8. Tab completion: 

### Put challenge description here

**Flag:** ``

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

# 9. 

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

# 10. 

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
