# description: 
You enter a virtual maze, a labyrinth of shifting corridors and endless paths. A guardian robot patrols the floor, leaving a trail behind as it moves. Follow the path it carves, trace its movements carefully, and uncover the key it leads you to. Only by following the robot’s trail can you reach the door to the next floor.
# writeup: 
flag:```citadel{p4th_tr4v3rs4l_m4st3ry_4ch13v3d}```

There was a website given in the description of the challenge. In the website, after clicking inspect, there was a website robots.txt whose display was blocked on the website. After going to robots.txt this was there 
```
User-agent: *

# We value our digital privacy and have restricted access to certain system-level configurations.
Disallow: /file?path=../../etc/passwd
Disallow: /file?path=../../../etc/passwd

# Hint for curious explorers: 
# Sometimes system files like /etc/passwd can reveal interesting information...
# But remember to respect privacy boundaries!
```
Since it told /etc/passwd can reveal interesting information, we went there. From here we went into different files based on the clues given and at last went to /home/ctf/.secret/flag.txt, which had the flag. 
