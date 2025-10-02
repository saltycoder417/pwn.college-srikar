# 1. Translating characters: 
### In this challenge, they they told that  /challenge/run will print the flag but will swap the casing of all characters (e.g., A will become a and vice-versa). We have to reverse the casing to get the flag. 

## My solve
**pwn.college{0DFMMoV88e8s58T-Pl3HAfisl-X.01MxEzNxwiN3kjNzEzW}**

I first connected the stdout of /challenge/run to the stdin of the tr command. I gave all capital letters and small letters as first argument and for the second argument, i kept small letter first, as we have to 
reverse the casing. 

```
hacker@data~translating-characters:~$ /challenge/run | tr ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
yOUR CASE-SWAPPED FLAG:
pwn.college{0DFMMoV88e8s58T-Pl3HAfisl-X.01MxEzNxwiN3kjNzEzW}
```

## What I learnt
I learnt about the tr command, which translates characters it receives over standard input and prints them to standard output. One way we can use it is that it translates the character provided in its first argument 
to the character provided in its second argument. For example: "tr a b", will translate all a's to b's. 

## References
pwn.college instructions.

# 2. Deleting characters: 
### In this challenge, they they told that  /challenge/run will print the flag but will intersperse some decoy characters (specifically: ^ and %) among the flag characters. They told us to use tr -d to remove them.

## My solve
**pwn.college{o9X5Y_b9z7KZSOPocR5mwLCT3S5.0FNxEzNxwiN3kjNzEzW}**

I first connected the stdout of /challenge/run to the stdin of the tr -d command. I gave "^%" as arguments, as we have to remove those characters from the output.  

```
hacker@data~deleting-characters:~$ /challenge/run | tr -d ^%
Your character-stuffed flag:
pwn.college{o9X5Y_b9z7KZSOPocR5mwLCT3S5.0FNxEzNxwiN3kjNzEzW}
```

## What I learnt
I learnt that tr can also translate characters to nothing (basically delete them). This is done via "-d" flag and an argument of what characters to delete. For example: "tr -d ab" will delete all a's and b's.

## References
pwn.college instructions.


# 3. Deleting newlines: 
### In this challenge, they told that /challenge/run has a bunch of newlines added into the flag. They told us to delete them using tr's -d flag and the escaped newline specification.

## My solve
**pwn.college{k2ANoCb8V3zqJqajuCbKLcFbrII.0VNxEzNxwiN3kjNzEzW}**

I first connected the stdout of /challenge/run to the stdin of the tr -d command. I then gave \n (newline specification) as argument in double quotes ("\n") to delete all the newlines and get the flag. 

```
hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{k2ANoCb8V3zqJqajuCbKLcFbrII.0VNxEzNxwiN3kjNzEzW}
```

## What I learnt
I learnt about the newline specification, which is "/n". We have to keep it in double quotes when we use it in tr command. Here, the backslash (\) signifies that the character that follows it is a standin for a character that's hard to input into the shell normally. Also, if you want to replace backslash (\) character, we have to use (\\). 

## References
pwn.college instructions.

# 4. Extracting the first lines with head: 
### In this challenge, they told that  /challenge/pwn outputs a bunch of data, and we need to pipe it through head to grab just the first 7 lines and then pipe them onwards to /challenge/college, which will give us the flag if we do this right. 

## My solve
**pwn.college{kMNji4WlThHZYOPp_HTeFEInWxh.0lNxEzNxwiN3kjNzEzW}**

I first connected the output of /challenge/pwn to the head command with -n 7 as argument to get the first 7 lines. I then connected this output to /challenge/college to get the flag. 

```
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{kMNji4WlThHZYOPp_HTeFEInWxh.0lNxEzNxwiN3kjNzEzW}
```

## What I learnt
I learnt about the head command, which can be used to  display the first few lines of its input. By default, it shows the first 10 lines, but we can control this with the -n option. For example: cat /something | head -n 10, will print the first 10 lines of "something" file. 

## References
pwn.college instructions.

# 5. Extracting specific sections of text: 
### In this challenge, they told that  /challenge/pwn outputs a bunch of data, and we need to pipe it through head to grab just the first 7 lines and then pipe them onwards to /challenge/college, which will give us the flag if we do this right. 

## My solve
****

I first connected the output of /challenge/pwn to the head command with -n 7 as argument to get the first 7 lines. I then connected this output to /challenge/college to get the flag. 

```
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{kMNji4WlThHZYOPp_HTeFEInWxh.0lNxEzNxwiN3kjNzEzW}
```

## What I learnt
I learnt about the head command, which can be used to  display the first few lines of its input. By default, it shows the first 10 lines, but we can control this with the -n option. For example: cat /something | head -n 10, will print the first 10 lines of "something" file. 

## References
pwn.college instructions.
