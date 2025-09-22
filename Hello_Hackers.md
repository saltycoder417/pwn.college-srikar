# 1. Intro to commands: 

### The challenge asked me to invoke my first command. We had to invoke the hello command to get the flag. 

**Flag:** `pwn.college{E4UAnd_PkpuSJLHKmRd9zGrv1OL.QX3YjM1wiN3kjNzEzW}`
## My solve: 
In the problem statement, it was provided that, using the 'hello' command would provide the flag. Hence i first connected my ubuntu terminal with pwn.college then i invoked hello command to get the flag.


```
hacker@hello~intro-to-commands:~$ hello
Success! Here is your flag:
pwn.college{E4UAnd_PkpuSJLHKmRd9zGrv1OL.QX3YjM1wiN3kjNzEzW}
```

## What I learned

I learnt about the whoami command in this. This command basically tells the username. I also learnt how to connect ssh key with pwn.college, you have to use 'ssh -i key hacker@dojo.pwn.college/whatever it tells over 
there' 

## References

The reference used was the problem statement itself in pwn.college. 

# 2. Intro to Arguments: 

### This challenge asked me to run a command along with an argument. The command given was hello and a single argument 'hackers' was asked to invoke.  

**Flag:** `pwn.college{M7kQWNzVTrI4P3yZ9duarps6yD_.QX4YjM1wiN3kjNzEzW}`
## My solve: 
In the problem statement, it was provided that, using the 'hello' command along with hackers argument the would provide the flag. Hence i first connected my ubuntu terminal with pwn.college then i typed 
'hello hackers' to get the flag.


```
hacker@hello~intro-to-arguments:~$ hello hackers
Success! Here is your flag:
pwn.college{M7kQWNzVTrI4P3yZ9duarps6yD_.QX4YjM1wiN3kjNzEzW}
```

## What I learned

I learnt what are elements in this challenge. I also learnt about the echo command, which just echoes/prints back all the arguments in the terminal. 

## References

The reference used was the problem statement itself in pwn.college. 

# 3. Command History: 

### The challenge asked me to check the command history. It kept the flag inside my history and i had to use either up or down arrow to search for the flag in the history. 

**Flag:** `pwn.college{QLJ_8ihsfUwhGVJlEQWBRnP2WQN.0lNzEzNxwiN3kjNzEzW}`
## My solve: 
I first conneceted ubuntu terminal with pwn.college. Then i started searching the command history using up and down arrows. After clicking the up arrow once, the flag was revealed.


```
hacker@hello~command-history:~$ the flag is pwn.college{QLJ_8ihsfUwhGVJlEQWBRnP2WQN.0lNzEzNxwiN3kjNzEzW}
```

## What I learned

I learnt that the shell saves a histroy of every command we invoke. We can navigate through the history using up and down arrows. 

## References

The reference used was the problem statement itself in pwn.college. 
