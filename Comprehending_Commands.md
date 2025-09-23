# 1. Cat: not the pet but the command: 

### In this challenge, they introduced us to the cat command. They copied the flag file to home directory and we had to read it using cat. 

**Flag:** `pwn.college{03xvramkBrv0_6MW_3P2dD4aGTy.QXxcTN0wiN3kjNzEzW}`

They told flag file is in home directory, so i used the cat command and the flag was given as output in the terminal. 

```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{03xvramkBrv0_6MW_3P2dD4aGTy.QXxcTN0wiN3kjNzEzW}
```

## What I learned

I learnt about the cat command, which is used to read out the files which are given as arguments. We can keep multiple arguments also. if you give no arguments at all, cat will read from the terminal input and output it.

## References

The references used were the problem statements in pwn.college, where they explained each command for each challenge. 

# 2. catting absolute paths: 

### In this challenge, The flag file was not copied to home directory, but it was readable with cat at it's absolute path. 

**Flag:** `pwn.college{Ew4ucrmOcZ7wAk2FihQc8y6MejD.QX5ETO0wiN3kjNzEzW}`

I ran the cat command with the absolute path of flag (/flag) as the argument and got the flag.

```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{Ew4ucrmOcZ7wAk2FihQc8y6MejD.QX5ETO0wiN3kjNzEzW}
```

## What I learned

We can use absolute paths as arguments in cat command along with relative paths. 

## References

The references used were the problem statements in pwn.college, where they explained each command for each challenge. 

# 3. more catting practice: 

### Over here, they told we cant use the cd command, and we have to retrieve the flag by absolute path. They told the directory the flag is in also.

**Flag:** `pwn.college{oZfeDzcumECToeF311f7jqw_-cx.QXwITO0wiN3kjNzEzW}`

I used the cat command with the absolute path of flag file as argument and got the flag.

```
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /usr/lib/emacsen-common/flag. Go cat it out **without** cding into
that directory!
hacker@commands~more-catting-practice:~$ cat /usr/lib/emacsen-common/flag
pwn.college{oZfeDzcumECToeF311f7jqw_-cx.QXwITO0wiN3kjNzEzW}
```

## What I learned

We can specify all sorts of paths as arguments to commands.

## References

The references used were the problem statements in pwn.college, where they explained each command for each challenge. 

# 4. grepping for a needle in a haystack: 

### In this challenge, the grep command was introduced. A file with huge number of words was given and they asked us to search for the flag in that. 

**Flag:** `pwn.college{srPiOABwY2xVatWTZXQrx9H0Wyf.QX3EDO0wiN3kjNzEzW}`

I used the grep command with pwn.college (since all flags over here start with that) and the absolute path of data.txt (the file they gave) as arguments and found the flag. 

```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{srPiOABwY2xVatWTZXQrx9H0Wyf.QX3EDO0wiN3kjNzEzW}
```

## What I learned

I learnt about the grep command, and 1 out of the many ways it can be used. It can be used to search a file for lines containing specific texts and print them. (usage: grep text_u_want_to_find /path/to/file).

## References

The references used were the problem statements in pwn.college, where they explained each command for each challenge. 

# 5. comparing files: 

### In this challenge, two files were given, 1 with 100 fake flags, and another with 100 fake flags and 1 real flag. We have to find the real flag.

**Flag:** `pwn.college{MpPIdx9H8R6CjpWZ3FP1SVJ8QmE.01MwMDOxwiN3kjNzEzW}`

I used the diff command with the two files they gave a arguments to find the difference between the two files and the flag was found, as it was the only difference between the two files.

```
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
30a31
> pwn.college{MpPIdx9H8R6CjpWZ3FP1SVJ8QmE.01MwMDOxwiN3kjNzEzW}
```

## What I learned

I learnt about the diff command. It compares two files line by line and shows you exactly what's different between them. We have to give the 2 files we want to compare as arguments. 

## References

The references used were the problem statements in pwn.college, where they explained each command for each challenge. 

# 6. listing files: 

### In this challenge, ls command was introduced. The '/challenge/run' was given a random name and kept in '/challenge' directory. We had to run the renamed program to get the flag.

**Flag:** `pwn.college{Y9cysKwdDfcdcp8R-sr1Xn-8Nvl.QX4IDO0wiN3kjNzEzW}`

I used the ls command in challenge directory, which lists all the files in the directory. The rennamed program was printed and then i ran the program to get the flag. I first thought this was a file and used
cat command but later realised it is a program which we have to run.

```
hacker@commands~listing-files:~$ ls /challenge
11587-renamed-run-17373  DESCRIPTION.md
hacker@commands~listing-files:~$ cat /challenge/11587-renamed-run-17373
#!/opt/pwn.college/bash

echo "Yahaha, you found me! Here is your flag:"
cat /flag
hacker@commands~listing-files:~$ /challenge/11587-renamed-run-17373
Yahaha, you found me! Here is your flag:
pwn.college{Y9cysKwdDfcdcp8R-sr1Xn-8Nvl.QX4IDO0wiN3kjNzEzW}
```

## What I learned

I learned about the ls command, which lists all the files in the directories which is given as arguments. If no files are given as argument, then it will list all the files of the current working directory.

## References

The references used were the problem statements in pwn.college, where they explained each command for each challenge. 

# 7. touching files: 

### In this challenge, They asked to create two new files and run '/challenge/run' to get the flag. The touch command was introduced.

**Flag:** `pwn.college{k46dOmbNYm3yJydC-DD42Gaxl0X.QXwMDO0wiN3kjNzEzW}`

I first changed the current working directory to tmp, since that was where they asked us to create the files. Then i used touch command to create the files they asked for and used ls command to confirm they were
created. I then ran the program and got the flag.

```
=hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ ls
bin  college  hsperfdata_root  pwn  tmp.TpSOPGOVKK
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{k46dOmbNYm3yJydC-DD42Gaxl0X.QXwMDO0wiN3kjNzEzW}
```

## What I learned

I learned about the touch command, which can be used to create a new, blank file. The name of the file is the argument you give to the command. 

## References

The references used were the problem statements in pwn.college, where they explained each command for each challenge. 

# 8. removing files: 

### in this challenge, they asked us to remove a given file from the home directory, and run '/challenge/check' to get the flag.

**Flag:** `pwn.college{k-c4fkdGNuVzeIcaqtFRSD5oRMw.QX2kDM1wiN3kjNzEzW}`

I first used ls command to check if the file we have to delete is there (not compulsory, idk why i did it), then i used the rm command with the name of the file as the argument to delete that file.

```
hacker@commands~removing-files:~$ ls
Desktop  delete_me  i
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ ls
Desktop  i
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{k-c4fkdGNuVzeIcaqtFRSD5oRMw.QX2kDM1wiN3kjNzEzW}
```

## What I learned

I learned about the rm command, which is used to delete files. To remove the file, you have to keep the name of the file as the argument. 

## References

The references used were the problem statements in pwn.college, where they explained each command for each challenge. 

# 9. moving files: 

### In this challenge, they asked us to move /flag file into '/tmp/hack-the-planet' directory then run '/challenge/check' to get the flag.

**Flag:** `pwn.college{gs8OrnZdnK0zncz_9phxU_bQrVg.0VOxEzNxwiN3kjNzEzW}`

I first used the mv command to move the file into the given directory, then ran the program to get the flag.

```
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{gs8OrnZdnK0zncz_9phxU_bQrVg.0VOxEzNxwiN3kjNzEzW}
```

## What I learned

I learned about the mv command, which is used to move files around. Usage: mv FILE_NAME DESTINATION.

## References

The references used were the problem statements in pwn.college, where they explained each command for each challenge. 

# 10. Hidden files: 

### In this challenge, the flag was hidden as a dot-prepended file in /. we have to find the flag.

**Flag:** `pwn.college{QzwPzPOFYH9royDUyhAhtlykMvS.QXwUDO0wiN3kjNzEzW}}`

I first used the ls command with -a and / as arguments. -a indicates to show hidden files also (files with dot-prepend (.FILENAME)). I then found the hidden flag file and used the cat command to read the flag.

```
hacker@commands~hidden-files:~$ ls -a /
.   .dockerenv             bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-195631507232274  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:~$ cat /.flag-195631507232274
pwn.college{QzwPzPOFYH9royDUyhAhtlykMvS.QXwUDO0wiN3kjNzEzW}}
```

## What I learned

I learned that ls doesn't list all the files by default. Linux has a convention where files that start with a '.' don't show up by default in ls.To view them with ls, you need to invoke ls with the -a flag.

## References

The references used were the problem statements in pwn.college, where they explained each command for each challenge. 

# 11. An epic filesystem quest: 

### This challenge is lengthy, with the knowledge of cd,ls, cat commands and also with the help of they clues they gave initially and also later, we have to find the flag. 

**Flag:** `pwn.college{g_vcRFqTGtXLzmKGs-_3w19BYbO.QX5IDO0wiN3kjNzEzW}`

With the help of the clues they gave, I played around with cd,ls,cat commands. I looked for odd looking file names (For all of them, all the letters were capital) and read those files (using cat and sometimes cd also) to find clues after clues, after a while of this the flag showed up.

```
hacker@commands~an-epic-filesystem-quest:~$ ls /
DOSSIER  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin      challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:~$ cat /DOSSIER
Congratulations, you found the clue!
The next clue is in: /usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/Latin-Modern/Marks/Regular
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/Latin-Modern/Marks/Regular
cat: /usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/Latin-Modern/Marks/Regular: Is a directory
hacker@commands~an-epic-filesystem-quest:~$ ls /usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/Latin-Modern/Marks/Regular
Main.js  SPOILER
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/Latin-Modern/Marks/Regular/SPOILER
Yahaha, you found me!
The next clue is in: /usr/share/sphinx/locale/de

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:~$ ls /usr/share/sphinx/locale/de
NUGGET  sphinx.js
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/share/sphinx/locale/de/NUGGET
cat: /usr/share/sphinx/locale/de/NUGGET: Permission denied
hacker@commands~an-epic-filesystem-quest:~$ cd /usr/share/sphinx/locale/de
hacker@commands~an-epic-filesystem-quest:/usr/share/sphinx/locale/de$ cat ./NUGGET
Congratulations, you found the clue!
The next clue is in: /opt/pwndbg/.venv/lib/python3.8/site-packages/dateutil/tz/__pycache__

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/share/sphinx/locale/de$ cd /opt/pwndbg/.venv/lib/python3.8/site-packages/dateutil/tz/__pycache__
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/dateutil/tz/__pycache__$ ls
POINTER                  _common.cpython-38.pyc     tz.cpython-38.pyc
__init__.cpython-38.pyc  _factories.cpython-38.pyc  win.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/dateutil/tz/__pycache__$ cat /opt/pwndbg/.venv/lib/python3.8/site-packages/dateutil/tz/__pycache__/POINTER
Congratulations, you found the clue!
The next clue is in: /opt/busybox/busybox-1.33.2/examples/var_service/fw

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/dateutil/tz/__pycache__$ ls /opt/busybox/busybox-1.33.2/examples/var_service/fw
TIP-TRAPPED  conf  etc  run  stat
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/dateutil/tz/__pycache__$ cat /opt/busybox/busybox-1.33.2/examples/var_service/fw/TIP-TRAPPED
Great sleuthing!
The next clue is in: /usr/share/doc/libxcb-dri3-0

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/dateutil/tz/__pycache__$ ls /usr/share/doc/libxcb-dri3-0
INFO-TRAPPED  changelog.Debian.gz  copyright
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/dateutil/tz/__pycache__$ cat /usr/share/doc/libxcb-dri3-0/INFO-TRAPPED
Tubular find!
The next clue is in: /usr/local/lib/python3.8/dist-packages/jedi/third_party/typeshed/third_party/2/kazoo

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/dateutil/tz/__pycache__$ ls -a /usr/local/lib/python3.8/dist-packages/jedi/third_party/typeshed/third_party/2/kazoo
.  ..  .TRACE  __init__.pyi  client.pyi  exceptions.pyi  recipe
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/dateutil/tz/__pycache__$ cat /usr/local/lib/python3.8/dist-packages/jedi/third_party/typeshed/third_party/2/kazoo/.TRACE
Yahaha, you found me!
The next clue is in: /usr/share/racket/pkgs/compatibility-lib/lazy

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/dateutil/tz/__pycache__$ ls -a /usr/share/racket/pkgs/compatibility-lib/lazy
.  ..  .HINT  compiled  mz-without-promises.rkt
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/dateutil/tz/__pycache__$ cat /usr/share/racket/pkgs/compatibility-lib/lazy/.HINT
Lucky listing!
The next clue is in: /usr/share/locale/ga

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/dateutil/tz/__pycache__$ cd /usr/share/locale/ga
hacker@commands~an-epic-filesystem-quest:/usr/share/locale/ga$ ls
LC_MESSAGES  README
hacker@commands~an-epic-filesystem-quest:/usr/share/locale/ga$ cat ./README
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{g_vcRFqTGtXLzmKGs-_3w19BYbO.QX5IDO0wiN3kjNzEzW}
```

## What I learned

I learned how and when to use ls, cd, cat commands properly.

## References

The references used were the problem statements in pwn.college. I also used the clues given after executing the commands in the terminal. 

# 12. making directories: 

### Put challenge description here

**Flag:** `pwn.college{MMBcU3wOEVfBOvLzoM1UyQ2a3YM.QXxMDO0wiN3kjNzEzW}`

explain your solve and how you got to it, explain any incorrect tangents you went on while solving.

to put code snippets, put three backticks and for images and all other stuff you wish to put here, refer to the documentation given to you.

don't style it too much, your solve should be readable and understandable by you so that when you have doubts, you refer to your own writeups, instead of gpt.

```
hacker@commands~making-directories:~$ cd /tmp
hacker@commands~making-directories:/tmp$ ls
bin  hsperfdata_root  tmp.TpSOPGOVKK
hacker@commands~making-directories:/tmp$ mkdir pwn
hacker@commands~making-directories:/tmp$ ls
bin  hsperfdata_root  pwn  tmp.TpSOPGOVKK
hacker@commands~making-directories:/tmp$ cd ./pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ ls
college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{MMBcU3wOEVfBOvLzoM1UyQ2a3YM.QXxMDO0wiN3kjNzEzW}
```

## What I learned

explain what you learned

## References

The references used were the problem statements in pwn.college, where they explained each command for each challenge. 

# 13. finding files: 

### Put challenge description here

**Flag:** `pwn.college{8QgHQnusu_mhRnEBEBymbs4Ackm.QXyMDO0wiN3kjNzEzW}`

explain your solve and how you got to it, explain any incorrect tangents you went on while solving.

to put code snippets, put three backticks and for images and all other stuff you wish to put here, refer to the documentation given to you.

don't style it too much, your solve should be readable and understandable by you so that when you have doubts, you refer to your own writeups, instead of gpt.

```
hacker@commands~finding-files:~$ find -name flag
hacker@commands~finding-files:~$ find / -name flag
find: ‘/root’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/tmp/tmp.TpSOPGOVKK’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/share/autoconf/Autom4te/flag
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/nix/store/7ns27apnvn4qj4q5c82x0z1lzixrz47p-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/5z3sjp9r463i3siif58hq5wj5jmy5m98-python3.12-pwntools-4.13.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/5n5lp1m8gilgrsriv1f2z0jdjk50ypcn-rizin-0.7.3/share/rizin/flag
/nix/store/bnlabj2vsbljhp597ir29l51nrqhm89w-rizin-0.7.4/share/rizin/flag
/nix/store/s8b49lb0pqwvw0c6kgjbxdwxcv2bp0x4-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/1hyxipvwpdpcxw90l5pq1nvd6s6jdi5m-python3.12-pwntools-4.14.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/h88mxp2mbgyj06vypwmqpy05idhwimnp-python3.13-pwntools-4.14.1/lib/python3.13/site-packages/pwnlib/flag
/nix/store/5qz6hgb1qzpvjrsw20wyiylx5zw8b9bk-pwntools-4.14.0/lib/python3.13/site-packages/pwnlib/flag
hacker@commands~finding-files:~$ cat /usr/local/lib/python3.8/dist-packages/pwnlib/flag
cat: /usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$ cat /usr/share/autoconf/Autom4te/flag
```

## What I learned

explain what you learned

## References

The references used were the problem statements in pwn.college, where they explained each command for each challenge. 

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

Add an references or videos you used while solving the challenge.

