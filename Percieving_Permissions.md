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
