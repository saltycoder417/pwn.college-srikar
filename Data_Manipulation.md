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

