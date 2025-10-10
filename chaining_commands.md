# 1. Chaining with semicolons: 
### In this challenge, they asked us to run /challenge/pwn and then /challenge/college, chaining them with a semicolon.

## My solve
**pwn.college{A_NZihqZd1BC4hQxZiqez6Mfr4E.QX1UDO0wiN3kjNzEzW}**

I ran /challenge/pwn and /challenge/college programs chained with a semicolon (;) to get the flag.

```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{A_NZihqZd1BC4hQxZiqez6Mfr4E.QX1UDO0wiN3kjNzEzW}
```

## What I learnt
I learned that we can chain commands with a semicolon (;). In most contexts, ; separates commands in a similar way to how Enter separates lines.

## References
pwn.college instructions.  

# 2. Building on success: 
### In this challenge, they asked us to chain the programs /challenge/first-success and /challenge/second using the "&&" operator.

## My solve
**pwn.college{I7wyRTbVKnfwWafsLSWRJwFgKgZ.0lM0MDOxwiN3kjNzEzW}**

I ran /challenge/first-success along with the AND operator (&&) and /challenge/second (/challenge/first-success && /challenge/second) to get the flag. 

```
hacker@chaining~building-on-success:~$ /challenge/first-success
hacker@chaining~building-on-success:~$ echo $?
0
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{I7wyRTbVKnfwWafsLSWRJwFgKgZ.0lM0MDOxwiN3kjNzEzW}
```

## What I learnt
I learned about the "&&" operator. It allows us to run a second command only if the first command succeeds (in Linux convention, this means it exited with code 0). syntax: "command1 && command2", this means run command1, and if it succeeds then run command2.  

## References
pwn.college instructions.  

# 3. Handling failure: 
### In this challenge, they asked us to chain the programs /challenge/first-failure and /challenge/second using the OR operator (||). 

## My solve
**pwn.college{A-5st5ivNQ3Jj49bq8o8hTtMukG.01M0MDOxwiN3kjNzEzW}**

I ran /challenge/first-failure along with the OR operator (||) and /challenge/second (/challenge/first-failure || /challenge/second) to get the flag. 

```
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{A-5st5ivNQ3Jj49bq8o8hTtMukG.01M0MDOxwiN3kjNzEzW}
```

## What I learnt
I learned about the OR (||) operator. It allows us to run a second command only if the first command fails (in Linux convention, this means it exited with a non zero code ). syntax: "command1 || command2", this means run command1, and if it fails then run command2.  

## References
pwn.college instructions.

# 4. Your first shell script: 
### In this challenge, they asked us to chain the programs /challenge/first-failure and /challenge/second using the OR operator (||). 

## My solve
****

I ran /challenge/first-failure along with the OR operator (||) and /challenge/second (/challenge/first-failure || /challenge/second) to get the flag. 

```
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{A-5st5ivNQ3Jj49bq8o8hTtMukG.01M0MDOxwiN3kjNzEzW}
```

## What I learnt
I learned about the OR (||) operator. It allows us to run a second command only if the first command fails (in Linux convention, this means it exited with a non zero code ). syntax: "command1 || command2", this means run command1, and if it fails then run command2.  

## References
pwn.college instructions.
