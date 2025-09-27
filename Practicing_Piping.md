# 1. Redirecting output: 

### This challenge asked us to write the word PWN (all uppercase) to the filename COLLEGE (all uppercase) using output redirection. 

**Flag:** `pwn.college{wTUyXlckMGJTjBgKqrxMi5JY9Mw.QX0YTN0wiN3kjNzEzW}`

I used the echo command with PWN as argument, then redirected the output to COLLEGE file using ">" to get the flag. 

```
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{wTUyXlckMGJTjBgKqrxMi5JY9Mw.QX0YTN0wiN3kjNzEzW}
```

## What I learned

I learned that every process in Linux has three initial, standard channels of communication: standard input (stdin), standard output (stdout), and standard error (stderr). These are the channels through which 
process takes input, processes output normal data, and processes output error details, respectively. We can redirect the standard output (stdout) to files using ">". For example, "echo hi > abcd" will redirect 
the output of echo hi (which will be hi) to the file abcd. We can then use a command like cat to read the file. 

## References

references used: challenge statements in https://pwn.college/linux-luminarium/piping/, https://www.rozmichelle.com/pipes-forks-dups/, 
https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/. 

# 2. Redirecting more output: 

### In this challenge, they asked us to redirect the output of /challenge/run to the "myflag" file, then the flag will be in that file. 

**Flag:** `pwn.college{UU31iFKt-lItUw5MY7HU8-ku6C5.QX1YTN0wiN3kjNzEzW}`

I first redirected the output of the /challenge/run program to the myflag file, then i read the file using cat command to get the flag. 

```
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat /flag
cat: /flag: Permission denied
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{UU31iFKt-lItUw5MY7HU8-ku6C5.QX1YTN0wiN3kjNzEzW}
```

## What I learned

I learned that we can redirect the output of any command to a file, not only echo. 

## References

references used: challenge statements in https://pwn.college/linux-luminarium/piping/, https://www.rozmichelle.com/pipes-forks-dups/, 
https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/. 

# 3. Appending output: 

### In this challenge, they asked us to  run /challenge/run with an append-mode redirect of the output to the file /home/hacker/the-flag. This will  write the first half of the flag to the file, and the second half to stdout. If you properly redirect in append-mode, the second half will be appended to the first, but if you redirect in truncation mode (>), the second half will overwrite the first and you won't get the flag.

**Flag:** `pwn.college{gaLrV3OEGHf44J3WS8MhLUFiCOJ.QX3ATO0wiN3kjNzEzW}`

I first redirected the output of /challenge/run to /home/hacker/the-flag, by appending it (using ">>" instead of ">"), as they told in the description. They told that if we redirect it properly, both first half 
and second half of the flag will get copied into the file, so i used the cat command to read the file and get the flag. 

```
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 |
\|/ This is the first half:
 v
pwn.college{gaLrV3OEGHf44J3WS8MhLUFiCOJ.QX3ATO0wiN3kjNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>)
rather than *append* mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!
```

## What I learned

I learned that if we use ">" to redirect an output, then it will create a new output file every time, deleting the old contents. If we want to append the output, that is add the output to the file without 
deleting the existing contents, we have to use ">>" instead of ">".

## References

references used: challenge statements in https://pwn.college/linux-luminarium/piping/, https://www.rozmichelle.com/pipes-forks-dups/, 
https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/.

# 4. Redirecting errors: 

### In this challenge, they asked us to redirect the output of /challenge/run, like before, to myflag, and the "errors" (in this case, the instructions) to instructions. Then they told we can find the instructions/feedback in instructions and the flag in myflag.

**Flag:** `pwn.college{sBKa9u9SX28qN_rzONKj34yw-qI.QX3YTN0wiN3kjNzEzW}`

I redirected the output of /challenge/run to myflag, as they told, by using ">", and redirected the errors to instructions by using "2>". I then read the myflag file using cat command to get the flag.

```
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{sBKa9u9SX28qN_rzONKj34yw-qI.QX3YTN0wiN3kjNzEzW}

hacker@piping~redirecting-errors:~$ cat instructions
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will check that error output is redirected to a specific file path : instructions
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!

[TEST] You should have redirected my stderr to instructions. Checking...

[PASS] The file at the other end of my stderr looks okay!
[PASS] Success! You have satisfied all execution requirements.
```

## What I learned

I learned about FD (file descriptor) number, it is a number that describes a communication channel in Linux. FD 0 is standard input, FD 1 is standard output, FD 2 is standard error. When you redirect process 
communication, you do it by FD number, though some FD numbers are implicit. For example, a > without a number implies 1>, which redirects FD 1 (Standard Output). If you want to redirect error, you have to use 
"2>", and similarly if you want to redirect output, you can use "1>" or ">". We can also redirect multiple file descriptors at the same time.  

## References

references used: challenge statements in https://pwn.college/linux-luminarium/piping/, https://www.rozmichelle.com/pipes-forks-dups/, 
https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/.

# 5. Redirecting inputs: 

### Put challenge description here

**Flag:** `pwn.college{kvxRXaJnOpaeME6Rc5E7kaVwKhe.QXwcTN0wiN3kjNzEzW}`

explain your solve and how you got to it, explain any incorrect tangents you went on while solving.

to put code snippets, put three backticks and for images and all other stuff you wish to put here, refer to the documentation given to you.

don't style it too much, your solve should be readable and understandable by you so that when you have doubts, you refer to your own writeups, instead of gpt.

```
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{kvxRXaJnOpaeME6Rc5E7kaVwKhe.QXwcTN0wiN3kjNzEzW}
```

## What I learned

explain what you learned

## References

references used: challenge statements in https://pwn.college/linux-luminarium/piping/, https://www.rozmichelle.com/pipes-forks-dups/, 
https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/.

# 6. grepping stored results: 

### Put challenge description here

**Flag:** `pwn.college{UZf8Dun3D-tIuGCqynb13bl0BC0.QX4EDO0wiN3kjNzEzW}`

explain your solve and how you got to it, explain any incorrect tangents you went on while solving.

to put code snippets, put three backticks and for images and all other stuff you wish to put here, refer to the documentation given to you.

don't style it too much, your solve should be readable and understandable by you so that when you have doubts, you refer to your own writeups, instead of gpt.

```
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep flag /tmp/data.txt
[FLAG] Here is your flag:
camouflaged
flags
conflagrations
flagellating
flagships
conflagration
flagellums
camouflage
flagons
flagella
flagon
flag
flagellated
flagellates
flag's
persiflage's
conflagration's
flagrant
flagon's
flagpole's
flagellum
camouflage's
flagellum's
flagellation's
flagstone
camouflaging
flagpoles
flagship's
flagpole
flagged
flagstones
flagellation
flagstaff
flagging
flagstone's
flagrantly
flagstaff's
persiflage
flagellate
flagship
unflagging
flagstaffs
camouflages
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{UZf8Dun3D-tIuGCqynb13bl0BC0.QX4EDO0wiN3kjNzEzW}
```

## What I learned

explain what you learned

## References

references used: challenge statements in https://pwn.college/linux-luminarium/piping/, https://www.rozmichelle.com/pipes-forks-dups/, 
https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/.

# 7. Grepping live output: 

### Put challenge description here

**Flag:** `pwn.college{wQuATaH7zQ7JKVkCuog1bbDVa50.QX5EDO0wiN3kjNzEzW}`

explain your solve and how you got to it, explain any incorrect tangents you went on while solving.

to put code snippets, put three backticks and for images and all other stuff you wish to put here, refer to the documentation given to you.

don't style it too much, your solve should be readable and understandable by you so that when you have doubts, you refer to your own writeups, instead of gpt.

```
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{wQuATaH7zQ7JKVkCuog1bbDVa50.QX5EDO0wiN3kjNzEzW}
```

## What I learned

explain what you learned

## References

references used: challenge statements in https://pwn.college/linux-luminarium/piping/, https://www.rozmichelle.com/pipes-forks-dups/, 
https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/.

# 8. Grepping errors: 

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

references used: challenge statements in https://pwn.college/linux-luminarium/piping/, https://www.rozmichelle.com/pipes-forks-dups/, 
https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/.

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

references used: challenge statements in https://pwn.college/linux-luminarium/piping/, https://www.rozmichelle.com/pipes-forks-dups/, 
https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/.

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

references used: challenge statements in https://pwn.college/linux-luminarium/piping/, https://www.rozmichelle.com/pipes-forks-dups/, 
https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/.

# 11. 

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

references used: challenge statements in https://pwn.college/linux-luminarium/piping/, https://www.rozmichelle.com/pipes-forks-dups/, 
https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/.

# 12. 

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

references used: challenge statements in https://pwn.college/linux-luminarium/piping/, https://www.rozmichelle.com/pipes-forks-dups/, 
https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/.

# 13. 

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

references used: challenge statements in https://pwn.college/linux-luminarium/piping/, https://www.rozmichelle.com/pipes-forks-dups/, 
https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/.

# 14. 

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

references used: challenge statements in https://pwn.college/linux-luminarium/piping/, https://www.rozmichelle.com/pipes-forks-dups/, 
https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/.
