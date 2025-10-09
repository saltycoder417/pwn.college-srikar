# 1. Changing file ownership: 
### In this challenge, they asked us to change the owner of /flag file to our username, that is hacker in pwn.college using chown command and then read the flag from that file. For this challenge only, they made it so that we can use chown to your heart's content as the hacker user (typically, this requires us to be root).

## My solve
**pwn.college{A3NiUy82xIBDlGHSWzKzvZDfZOL.QXxEjN0wiN3kjNzEzW}**

I first used the chown command and changed the owner of /flag file to hacker from root. Then as i was now the owner of the file, i could read it using cat command and get the flag.

```
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{A3NiUy82xIBDlGHSWzKzvZDfZOL.QXxEjN0wiN3kjNzEzW}
```

## What I learnt
I learned about the chown command, which is used to change the ownership of a file from one user to another. Generally, we need to be root to use this command. We can also check the permissions of a file or directory using ls -l.

## References
pwn.college instructions, also videos over there.  

# 2. Groups and files: 
### In this challenge, they asked us to change the group ownership of the /flag file to whatever group the user is in, and then read the file for the flag. They told that the flag is readable by whatever group owns it. They also told that it is possible in this challenge to invoke chgrp as the hacker user. 

## My solve
**pwn.college{kImWPPWaejiup302i_ZWJzURCmT.QXxcjM1wiN3kjNzEzW}**

I first used the id command to see what groups im in. Then i used the chgrp command to change the group ownership of /flag file to hacker group from root. I then read the file using cat command to get the flag.

```
hacker@permissions~groups-and-files:~$ id
uid=1000(hacker) gid=1000(hacker) groups=1000(hacker)
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{kImWPPWaejiup302i_ZWJzURCmT.QXxcjM1wiN3kjNzEzW}
```

## What I learnt
I learned about the chgrp command, which is used to change the group ownership of a file. syntax: chgrp "group name" "file name". I also learned that we can check what groups you are part of with the id command. 

## References
pwn.college instructions, also videos over there.  

# 3. Fun with group names: 
### In this challenge, they told that they have randomized the name of the group that your user is in. Like the previous level, we have to use the id command to figure that name out, then use chgrp and access /flag file.

## My solve
**pwn.college{oh7QrFgYgfrnIc2NB8dUMEVxOla.QXycjM1wiN3kjNzEzW}**

I first used the id command to see what groups im in. Then i used the chgrp command to change the group ownership of /flag file to grp8005 group from root. I then read the file using cat command to get the flag.

```
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp8005) groups=1000(grp8005)
hacker@permissions~fun-with-groups-names:~$ chgrp grp8005 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{oh7QrFgYgfrnIc2NB8dUMEVxOla.QXycjM1wiN3kjNzEzW}
```

## What I learnt
I learned when to use the chgrp command.  

## References
pwn.college instructions, also videos over there.

# 4. Changing permissions: 
### In this challenge, they told we have to change the permissions of the flag file and then read it to get the flag.  

## My solve
**pwn.college{cVX1L8QXYU7uwwEFM91J4t5CR8L.QXzcjM1wiN3kjNzEzW}**

I used the chmod command with o+r as argument, as other users have 

```
hacker@permissions~changing-permissions:~$ chmod o+r
chmod: missing operand after ‘o+r’
Try 'chmod --help' for more information.
hacker@permissions~changing-permissions:~$ chmod o+r *
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{cVX1L8QXYU7uwwEFM91J4t5CR8L.QXzcjM1wiN3kjNzEzW}
```

## What I learnt
I learned when to use the chgrp command.  

## References
pwn.college instructions, also videos over there.

# 5. Executable file: 
### In this challenge, they told we have to change the permissions of the flag file and then read it to get the flag.  

## My solve
**pwn.college{IwO0R6YQIQw4000aFJy5yY2SYtE.QXyEjN0wiN3kjNzEzW}**

I used the chmod command with o+r as argument, as other users have 

```
hacker@permissions~executable-files:~$ ls -l /challenge/run
-r--r--r-- 1 hacker hacker 32 Jan 14  2025 /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
bash: /challenge/run: Permission denied
hacker@permissions~executable-files:~$ chmod o+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
bash: /challenge/run: Permission denied
hacker@permissions~executable-files:~$ ls -l /challenge/run
-r--r--r-x 1 hacker hacker 32 Jan 14  2025 /challenge/run
hacker@permissions~executable-files:~$ chmod a+x /challenge/run
hacker@permissions~executable-files:~$ ls -l /challenge/run
-r-xr-xr-x 1 hacker hacker 32 Jan 14  2025 /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{IwO0R6YQIQw4000aFJy5yY2SYtE.QXyEjN0wiN3kjNzEzW}
```

## What I learnt
I learned when to use the chgrp command.  

## References
pwn.college instructions, also videos over there.

# 6. Permission tweaking practise: 
### In this challenge, they told we have to change the permissions of the flag file and then read it to get the flag.  

## My solve
****

I used the chmod command with o+r as argument, as other users have 

```
hacker@permissions~changing-permissions:~$ chmod o+r
chmod: missing operand after ‘o+r’
Try 'chmod --help' for more information.
hacker@permissions~changing-permissions:~$ chmod o+r *
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{cVX1L8QXYU7uwwEFM91J4t5CR8L.QXzcjM1wiN3kjNzEzW}
```

## What I learnt
I learned when to use the chgrp command.  

## References
pwn.college instructions, also videos over there.

# 4. Changing permissions: 
### In this challenge, they told we have to change the permissions of the flag file and then read it to get the flag.  

## My solve
**pwn.college{cVX1L8QXYU7uwwEFM91J4t5CR8L.QXzcjM1wiN3kjNzEzW}**

I used the chmod command with o+r as argument, as other users have 

```
hacker@permissions~changing-permissions:~$ chmod o+r
chmod: missing operand after ‘o+r’
Try 'chmod --help' for more information.
hacker@permissions~changing-permissions:~$ chmod o+r *
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{cVX1L8QXYU7uwwEFM91J4t5CR8L.QXzcjM1wiN3kjNzEzW}
```

## What I learnt
I learned when to use the chgrp command.  

## References
pwn.college instructions, also videos over there.

# 4. Changing permissions: 
### In this challenge, they told we have to change the permissions of the flag file and then read it to get the flag.  

## My solve
**pwn.college{cVX1L8QXYU7uwwEFM91J4t5CR8L.QXzcjM1wiN3kjNzEzW}**

I used the chmod command with o+r as argument, as other users have 

```
hacker@permissions~changing-permissions:~$ chmod o+r
chmod: missing operand after ‘o+r’
Try 'chmod --help' for more information.
hacker@permissions~changing-permissions:~$ chmod o+r *
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{cVX1L8QXYU7uwwEFM91J4t5CR8L.QXzcjM1wiN3kjNzEzW}
```

## What I learnt
I learned when to use the chgrp command.  

## References
pwn.college instructions, also videos over there.

