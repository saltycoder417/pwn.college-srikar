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
### In this challenge, they told that /challenge/run program will give a bunch of lines with random numbers and single characters (characters of the flag) as columns. They asked us to use cut to extract the flag characters, then pipe them to tr -d "\n" (like the previous level!) to join them together into a single line to get the flag. 

## My solve
**pwn.college{82KSht-JjKmYz-Ve8WW08g29w4k.01NxEzNxwiN3kjNzEzW}**

I first ran the /challenge/run program to see the output. The 6th coloumn had the flag. I then connected the output of the program to the input of cut command to get with (-d " " -f 6) as argument to get the 6th coloumn. I then connected that output with the input of tr command with -d "\n" as argument to remove all the newlines and get the flag in 1 line. 

```
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run
3103 p
1584 w
22569 n
27832 .
12483 c
25098 o
14302 l
27485 l
11093 e
31698 g
15428 e
8706 {
17880 8
732 2
15520 K
20659 S
13092 h
4613 t
7282 -
8106 J
305 j
23324 K
6152 m
25300 Y
26592 z
11228 -
2027 V
27413 e
13981 8
12384 W
2867 W
303 0
14723 8
31414 g
27301 2
13677 9
6303 w
31931 4
3820 k
14354 .
24707 0
23303 1
22040 N
29942 x
25220 E
1330 z
18825 N
25685 x
17645 w
10809 i
1404 N
16368 3
15273 k
1742 j
22298 N
32412 z
23123 E
7219 z
632 W
17189 }
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{82KSht-JjKmYz-Ve8WW08g29w4k.01NxEzNxwiN3kjNzEzW}
```

## What I learnt
I learnt about the cut command, which can be used to extract a specific coloumn. The -d argument specifies the column delimiter (how columns are separated). The -f argument specifies which coloumn should be extracted. 

## References
pwn.college instructions.

# 6. Sorting data: 
### In this challenge, they told that /challenge/flags.txt has 100 fake flags, with the real flag mixed among them. When sorted alphabetically, the real flag will be at the end.  

## My solve
**pwn.college{kv42yVOk_xpRWcHV4d1G4i0dUQz.0FM0MDOxwiN3kjNzEzW}**

I used the sort command on /challenge/flags.txt, which will sort the file alphabetically, then the flag was at the last. 

```
hacker@data~sorting-data:~$ sort /challenge/flags.txt
ovm.bolkege{kv41xVOk_woRWcHV3c1F4i0dUPz.0FL0MDNxviN3kiNzEyW}
ovm.bolldgd{kv41yVNk_xoRWbHV4c1G3i0dTQy.0FM0LCOxwiN3kjNzEzW}
ovm.bollege{kv32yVOk_xoRWbHV4c0G3h0cUQy.0EL0MDNwwiN2kjMzEzW}
ovn.bolkdge{jv32yVNj_woQWcGV4c1G4h0dUQy.0EL0LDOxviN3kiNzDzW}
ovn.colkege{ju42xVOk_xpQWcHV3d1G4i0dUPz.0FL0MCNxwiN2kjMzEzV}
ovn.collefd{jv41xVOk_wpRWbGV4d1G3i0dTQz.0FL0MDOwviN3kjNzDzV}
owm.bollege{kv41yUOk_xpRWcHV3d1G4h0dUQy.0FL0MCOwwhN3jjMzEzW}
owm.colkege{kv42xVOk_xoQWcHV4d1G4h0dTQy.0FL0LDOwwhN3kiMzEzV}
owm.college{ju32yUOk_woRVcHV4d0G3i0dUPz.0FM0LDOxwiM3kiNzDzW}
owm.college{kv42xVOj_xoRWcHU4d1G4i0dUQy.0FL0MDOxwiN3kjMzDzV}
own.bollegd{ku42yVOk_xpRWcGU3d1G3i0dTQz.0FL0MDNxwiM2kjMyDzW}
own.bollege{jv42yVOk_xpRWbHV4d0G4h0dUQz.0EM0LDOxwiN3kjNzEzV}
own.cnklegd{kv42xUOk_xpQVcHU3d0G3h0dUPy.0EL0MDOxwiN2kjMzEyV}
own.cnlkdgd{jv32xVNj_xpRWbHV3d1G4i0dTPz.0FM0MCOxwhM3kiMzDzW}
own.cnlkege{kv42xVOj_wpRVbHV4d1G3i0dUQz.0FM0MDNwviN3kiNyEzV}
own.cnlldfe{kv42yVOj_xoRWcHU4c0G4i0dUQz.0EM0LDOxwhN3jjNyDyW}
own.coklegd{kv42yVOk_woRWbHV4d1F4i0dUQz.0FM0MDOxviN2kjNyEzW}
own.colkdgd{ku42yVOk_xpQWcGV4d1F4h0dUPz.0FM0MCOxviN2kjMzEyW}
own.colkefd{kv42xVOj_xoRWbHV3d1F4i0dUQy.0FL0MDOxwhN3kjMzDzW}
own.colkege{kv42yVNj_xoRWbHV4d0G4i0dUQz.0FL0MDOxwiN3kjNyEyW}
own.collegd{ku41yVNk_woRWcGV4d1G4h0cUQy.0EM0MDNxvhN3kiNzEzV}
own.college{ju42yUOj_wpRVcGV3d1G4h0dUQz.0FM0MDOxwiN3kjNyEzV}
own.college{jv42yVNk_xpQWcGV4d1G4i0dUQz.0EM0MDOxwhM3kjMzEzW}
own.college{kv31yUOk_wpRVcGV4d0G3h0dUQz.0FM0LCOxwhN3jiMzEyV}
own.college{kv32yUOj_xpQWcHV4d0G4i0dUQy.0EM0MDOxwiM2kjMzEzW}
own.college{kv42xVOk_xpRWcHV4c1F3i0dUPy.0FM0LCNxviN3kiNyEzW}
pvm.bollegd{jv31yVOk_xpRVbHV4d1F4h0cTQy.0EM0MDOxviM2kjMyEyW}
pvm.cnlkdge{kv41yVOk_xoRVcHV3d1G4i0dUQz.0FM0MCNxviM3jiNzDzW}
pvm.cnlkege{jv42xUOk_xpRWcGV4d1G4i0dUQy.0FM0MDNwwhN2jjMzDyW}
pvm.colldge{kv31yUOj_wpQWbHV4d1G3h0dTQy.0EM0MCOxwiN2jjNzEzW}
pvm.collefd{ju42yUOk_xpRWcHU4d1G4i0dUPz.0FL0MCOxwhN3kjMzEzW}
pvn.bnklefd{jv41xVNk_xpRWbGV4c0G4i0dUPz.0FL0MDNwwiM2kiNzEzW}
pvn.bnlkefd{ku42yVOk_woRVcGU3d1F4i0cTQz.0EL0MDOwwiM3kiMzDzV}
pvn.bolkege{kv31xVOk_xpRWcHU4c0G4i0dTQz.0FM0LCNxvhN2jjNyEzV}
pvn.cnlkefe{ku42xVNk_xpQVcGU4d0G4i0dUQz.0FL0MDNxwiM2jiMzDyV}
pvn.cnlkege{ku42xVOk_wpQWbHU4d1G4h0dTQy.0EL0MDOxwiN3kjNzEzW}
pvn.cnllege{kv42yVOk_xpRWcHV4c1G4i0dUQz.0FM0MDOxwiN3kjNzEzW}
pvn.cokkdge{kv42yVOk_woRVcHV3c0G3i0dUQy.0FL0MCOxwiN2kjNzEzW}
pvn.cokkefe{ku32yVOk_xpRVcGV4d1G3h0cTQy.0FM0LCOxwiM3jjNyDzW}
pvn.coklefe{kv32yVNj_wpQVcHU4d1G4i0cUPz.0FL0MCOxwiN3jjNzEyW}
pvn.college{ju42yUOj_wpRWbHU3d1G3i0dUQz.0EL0LDOwwiN3kiMzDzW}
pvn.college{ku42xVOk_xpRWcHV4d0G4h0dUQz.0FM0MDNxviN3kjNzEyW}
pvn.college{kv41xUOk_xpRWcHV4d1G4i0dUQz.0FM0MDOxwiM3jjNzEzW}
pvn.college{kv42xVNk_xpRWcHU3d1G4i0dUPz.0EM0LDOxviN3kiNzEzW}
pvn.college{kv42yVOk_xpRWcHV4d1F4i0dUQz.0FM0LDOwwiN3kjNzEzW}
pwm.bnklege{ju32yUOj_xoQWcHV4d1G3i0cUQz.0FM0LDNwviN3jjMzEzW}
pwm.bokkege{ku41yUOj_wpRVcGU4d1F4i0dUQz.0FM0MCOxviN3kjNyDyV}
pwm.bolkefe{ku42xUOj_xpRWcHU4d1G3i0dTQy.0EL0MDOwwhM3kjMzDzW}
pwm.cnllefe{ku41yVOk_xoRWbGV3d1F4h0cUPz.0FM0MCOwwhN2jjNzDzW}
pwm.cokldgd{ku42yVOk_xoRVcHV4d1F4i0cTQz.0FL0LCOxviM3kjNyDzW}
pwm.coklege{kv42yVOj_xpQWcHV4d1G3i0cUQz.0EM0LDOxwiN3kiNyDzW}
pwm.colldgd{kv42yVNk_wpRWcHV4d0F4i0cUQz.0FM0MDOxwhN3jjNzEzV}
pwm.collefe{kv32xVOj_xoQWcHV3d1G3i0dUPz.0FM0LCNxwhN3kiMzEzV}
pwm.college{kv41yVOj_xpRWcHU4d1F4i0cUQy.0FM0LDOxwhM3kiMzEzW}
pwn.bnkkege{kv42yVOk_woRWbHV3d0G4h0cUQy.0FL0MCOwwiN3jjNyEyW}
pwn.bnkldfe{jv42xVNk_xpQWcGV3c0G4i0cTQz.0EM0LDOxviM3kjNzEyV}
pwn.bnlkegd{ku41yUNj_xoRWbHV4d1F3i0dUQz.0FM0LDNxwhN2kjNyEzV}
pwn.bnllefe{kv42yVOk_wpQWcHV4d1G4i0cTQz.0FM0MDOxviN3jjNzEzW}
pwn.bnllege{ku32yVNj_xpQWcHV4d1G4i0cUQz.0FL0MCNxwiN3jjNzEyW}
pwn.boklege{kv31yVOk_xoRWcHV4d1G4i0dTQz.0FM0MDNxwiN3kjNzEzW}
pwn.bolkege{jv32xVNk_xpRWcHV3c1F4h0cUPz.0EL0MDOxwiM2jjMzDzV}
pwn.bolkege{kv32yVOk_xpRWcHV4c1G4i0dUQz.0FM0LDOxwiN3kiNzEzV}
pwn.bollefe{kv42yVOk_xpRWcHU4c1G4i0dTQz.0FL0MDOxviN3kiNzEzW}
pwn.cnlkdfe{ju42yUOk_xpRWcHV3d0F4i0dTQz.0EM0MCOxwiM3jiNzEyW}
pwn.cnlkege{kv31xVOj_xpRWbHU4d1F3h0dUQz.0FL0LCNxwhN3kiNzEzW}
pwn.cnllege{kv42yUOj_xpQVcHV4d1F3h0dTQy.0EL0LCNxwhN2kjNzEzW}
pwn.cnllege{kv42yVOj_wpQVbHV4c0G4i0dUQz.0FM0MCOxwiN3jjMyEzW}
pwn.cnllege{kv42yVOk_xpRWcGU4d1G4i0dUQz.0EM0MDOxwhN3kjNzEyW}
pwn.cokkdge{kv42xUOk_xpRWcHV3d1G3h0dUQy.0FL0MDNxwiN3kiNzEyW}
pwn.cokldge{kv42yUOk_xoRVcGV4c1G3i0cUQz.0FL0MCNxwiN3jjNzEzW}
pwn.coklefe{jv42yVOk_wpRWcGV4d1G4i0dTQz.0FL0MDOxvhN3kjMzEzW}
pwn.coklefe{ku32yVNj_woRVbGV4d1G3i0cUPy.0FM0MDNwviN2kjNzDzV}
pwn.coklefe{kv42yVOj_wpRVcGV3d0G3h0cUQy.0FL0LDOwwiN2jjMyDzW}
pwn.coklege{kv42yVOk_xpRWcHV4d1G4i0dTPz.0FL0MCOxwiM3kjNzEyW}
pwn.colkefe{kv42yVOk_xpRWcHV4d1G4i0dUQz.0FM0MDOxwhN3jjNzEzW}
pwn.colkege{ju42yUOk_xpRWcHV4c1F4h0cUPy.0FM0MDOxwhN3kiNzEyW}
pwn.colkege{jv42yUOk_wpRWcHV4d1G4i0cUQz.0FL0MDOxviN3kiMyDzV}
pwn.colkege{kv42yVOk_xoRVbHV3d1G4h0dUPz.0FM0MDOxwiN3jjNzEzW}
pwn.colldfe{ku31yVOk_woRWcHU4d0F4i0dUPz.0EL0MDOwwhN2kjNzEzW}
pwn.colldge{jv42yVOk_wpRWcHV4d1G4i0dUQz.0FM0MDOxwiN3kjNyEzV}
pwn.colldge{kv42xVNk_xpRWcHV4d1G4i0dUQz.0FM0MDOxwiN3jiMzEzW}
pwn.colldge{kv42yUOk_xpRWcHU4d1G4h0cUQz.0FM0MDOxwiN2kjNzDzV}
pwn.collegd{kv41yVOk_xpQWcHV4d1G3i0dTPz.0EM0LDOwwhN3jiNyDzV}
pwn.college{jv42xVOj_xoQWbHV4d1G4i0dUPy.0FM0MCNxvhM3jiNyEyW}
pwn.college{jv42yVOj_xpRWbHV4d1F4i0dUQz.0FM0MDOxwiN3kjNzEzW}
pwn.college{jv42yVOk_xpRWcHV4d1G4i0dUQz.0FM0MCOwviN3kjNzEzW}
pwn.college{kv32yVOk_xpRWcHV4d1G4i0dUQz.0FM0MDOxwiN3kjNzEzW}
pwn.college{kv41xVNk_xpQWcHU4d1G3i0dUQz.0FM0MDOwwhN2kjNyEzW}
pwn.college{kv41xVOk_xpRWcHV3d1G4h0dUQz.0FM0MDOxviN3kjNzEzW}
pwn.college{kv41yVOk_xpRWcHV4d1G4i0dTPz.0FM0MCOxwiN3jjNzEzW}
pwn.college{kv42yUOk_wpRWcHV3d1G4i0cUQz.0FM0LDOxwiN3kjNzEzW}
pwn.college{kv42yVNj_xpRWcHV4d0G4i0dUQy.0EM0LDNwwiN2kjNzEzW}
pwn.college{kv42yVOk_wpQWcHV4d1G4i0dUQz.0FM0LDOxwiN3kjNyEzW}
pwn.college{kv42yVOk_xpQWcHV4d1G4i0dUQz.0FM0MDOxwiN3kjNzEzW}
pwn.college{kv42yVOk_xpRVbHV4d1G4i0dUQz.0FM0MDOxwiN3kjNzEzW}
pwn.college{kv42yVOk_xpRWbHV4d1F4h0dTPz.0FL0MDOxwiN2kjNzEzW}
pwn.college{kv42yVOk_xpRWcHV3d1G4i0dUQz.0FM0MDOxwiN3kjNzEzW}
pwn.college{kv42yVOk_xpRWcHV4d0G4i0dTQz.0FM0MDOxwhN3jjNyEzW}
pwn.college{kv42yVOk_xpRWcHV4d0G4i0dUQz.0FL0MDOxwiN3kjNzEzW}
pwn.college{kv42yVOk_xpRWcHV4d1G4i0dUQz.0FL0MDOxwiN3kiMzEzW}
pwn.college{kv42yVOk_xpRWcHV4d1G4i0dUQz.0FM0MDOxwiN3kjNzEzW}
```

## What I learnt
I learnt about the sort command, which by it's name, sorts the data. By default, sort orders lines alphabetically. However, we can use arguments to change this like -r: reverse order (Z to A), -n: numeric sort (for numbers), -u: unique lines only (remove duplicates), -R: random order. 

## References
pwn.college instructions.
