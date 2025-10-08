# 1. Becoming root with su: 
### In this challenge, they asked us to become the root with su and then read the flag. The root password was given (hack-the-planet).

## My solve
**pwn.college{UoRZtY1xvQKJw6k9dOjtR38KXUi.QX1UDN1wiN3kjNzEzW}**

I first used su and then entered the password to become the root. I then read the flag file using cat command. 

```
hacker@users~becoming-root-with-su:~$ su
Password: 
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{UoRZtY1xvQKJw6k9dOjtR38KXUi.QX1UDN1wiN3kjNzEzW}
```

## What I learnt
I learned how we can become the root of the system using su command. su asks for a password before giving you root status. This check against the root password is what obsoletes su. Modern systems very rarely have root passwords, and different mechanisms (that we will learn later) are used to grant administrative access. su and sudo are the two utilities we can use to become the root.

## References
pwn.college instructions.

# 2. Other users with su: 
### In this challenge, they asked us to switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

## My solve
**pwn.college{sNbu9JPInrjvOzBy6WWXhwP1Nfy.QX2UDN1wiN3kjNzEzW}**

I first used su with zardus as argument and typed the password they gave to switch to zardus user. After switching, i ran /challenge/run to get the flag. 

```
hacker@users~other-users-with-su:~$ su zardus
Password: 
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{sNbu9JPInrjvOzBy6WWXhwP1Nfy.QX2UDN1wiN3kjNzEzW}
```

## What I learnt
I learned how we can switch users with su. We have to keep the username as the argument of the su command.

## References
pwn.college instructions.

# 3. Cracking passwords: 
### In this challenge, they gave us a leak of /etc/shadow in /challenge/shadow-leak. They then asked us to crack the password of zardus, then su to zardus and then run /challenge/run to get the flag. 

## My solve
**pwn.college{w87VXMpsPZ86kSV7mAF3TO5iTHt.QX3UDN1wiN3kjNzEzW}**

I first used the famous John the ripper on /challenge/shadow-leak to crack passwords. I also used the --show argument later to arrange it properly and i found the password of zardus. I then switched the user to zardus using su and entering the password found and ran /challenge/run to get the flag. 

```
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Created directory: /home/hacker/.john
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:12 0% 2/3 0g/s 270.4p/s 270.4c/s 270.4C/s leslie..boston
0g 0:00:00:14 0% 2/3 0g/s 271.5p/s 271.5c/s 271.5C/s francine..me
aardvark         (zardus)
1g 0:00:00:21 100% 2/3 0.04710g/s 274.2p/s 274.2c/s 274.2C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak --show
hacker:NO PASSWORD:20357:0:99999:7:::
zardus:aardvark:20369:0:99999:7:::

2 password hashes cracked, 0 left
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{w87VXMpsPZ86kSV7mAF3TO5iTHt.QX3UDN1wiN3kjNzEzW}
```

## What I learnt
I learned how we can crack passwords using john. The passwords used to be stored in /etc/passwd, but because /etc/passwd is a globally-readable file, this is not good for passwords, these were moved to /etc/shadow. The passwords in the file are generally encrypted. 

## References
pwn.college instructions and https://www.cyberciti.biz/faq/understanding-etcshadow-file/
