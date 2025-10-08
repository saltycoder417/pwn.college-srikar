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
### In this challenge, they asked us to become the root with su and then read the flag. The root password was given (hack-the-planet).

## My solve
**pwn.college{sNbu9JPInrjvOzBy6WWXhwP1Nfy.QX2UDN1wiN3kjNzEzW}**

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
