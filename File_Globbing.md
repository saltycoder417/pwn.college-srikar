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

### In this challenge, they copied the flag into /challenge/pwncollege, and we can freely cat that file. But we can't type the filename. We have to tab-complete (click tab on your keyboard) to get the flag.

**Flag:** `pwn.college{08Fvd-cOpIIqTNi2Nbp5morFro3.0FN0EzNxwiN3kjNzEzW}`

I read /challenge/pwncollege using the cat command, but i clicked tab after typint till pwn, as they told we muct tab-complete in the challenge to get the flag. 

```
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​
pwn.college{08Fvd-cOpIIqTNi2Nbp5morFro3.0FN0EzNxwiN3kjNzEzW}
```

## What I learned

I learned that instead of using the star glob, which is risky as it might expand to unintended files, we can click tab when we are writing the path of the file and the shell will try to figure out what you're going to type and automatically complete it. All we have to do is click tab.

## References

The reference i used is the challenge statement in pwn.college.

# 9. Multiple options for tab completion: 

### In this challenge, there is a /challenge/files directory with a bunch of files starting with pwncollege. It was given we have to Tab-complete from /challenge/files/p or so, and make your way to the flag.

**Flag:** `pwn.college{EAWwMFN4A1IkLem0IZ8MGCM-OKv.0lN0EzNxwiN3kjNzEzW}`

I first typed till /challenge/files/pwncollege- then clicked tab, it then showed me a bunch of files starting with pwncollege-. I then tried reading a few with cat command, then when i went to /challenge/files/pwncollege-fl and clicked tab, it showed two options (flamingo and flag). I then read the flag file to get the flag.

```
hacker@globbing~multiple-options-for-tab-completion:~$ /challenge/files/pwncollege-
pwncollege-family      pwncollege-flamingo    pwncollege-flyswatter  pwncollege-hacking
hacker@globbing~multiple-options-for-tab-completion:~$ /challenge/files/pwncollege-family
/challenge/files/pwncollege-family: /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/share/bashdb/bashdb-main.inc: No such file or directory
/challenge/files/pwncollege-family: warning: cannot start debugger; debugging mode disabled
/challenge/files/pwncollege-family: line 1: No: command not found
hacker@globbing~multiple-options-for-tab-completion:~$ /challenge/files/pwncollege-hacking
/challenge/files/pwncollege-hacking: /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/share/bashdb/bashdb-main.inc: No such file or directory
/challenge/files/pwncollege-hacking: warning: cannot start debugger; debugging mode disabled
/challenge/files/pwncollege-hacking: line 1: No: command not found
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-family
No flag in this file!
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-hacking
No flag in this file!
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-fla
pwncollege-flag      pwncollege-flamingo
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-flag
pwn.college{EAWwMFN4A1IkLem0IZ8MGCM-OKv.0lN0EzNxwiN3kjNzEzW}
```

## What I learned

I learned that if there are more than 1 options when u click tab, then the bash will auto expand till the point where there are multiple options, or till the last common point of the multiple options, then if u hit agin for a second time, some bashes will cycle through all the options and some will show all the options available. 

## References

The reference i used is the challenge statement in pwn.college.

# 10. Tab completion on commands: 

### In this challenge, it was given that there is a command that starts with  pwncollege, and it'll give you the flag. It told us to type pwncollege and hit the tab key to auto-complete it.

**Flag:** `pwn.college{kGAJMVH5km2QeiuIQ-XxKJgQWtR.0VN0EzNxwiN3kjNzEzW}`

As given in the challenge statement, i first typed pwncollege then clicked tab, it auto completed the command and i executed the command to get the flag. 

```
hacker@globbing~tab-completion-on-commands:~$ pwncollege-25861
Correct! Here is your flag:
pwn.college{kGAJMVH5km2QeiuIQ-XxKJgQWtR.0VN0EzNxwiN3kjNzEzW}
```

## What I learned

I learned that we can use the tab key for completing not only files, but we can use it for commands also. But we must be careful when we auto complete and check if the command is correct to prevent wrong commands with a similar name from being executed. 

## References

The reference i used is the challenge statement in pwn.college.
