# description: 
Your quest continues, but you feel something odd about this room. The only artifact on this floor is a corrupted file held in the hands of a jet-black statue, frozen in the pose of a band mid-performance. The passcode to the next floor is hidden within this piece of music, but it can’t be played, as if the wrong extension has scrambled it.

You must take the corrupted file and repair it to reveal the true code that will unlock the door forward.
# writeup: 
flag:```citadel{8lackM1D1wa5c00l}```

In this challenge, a corrupted wav file was given. When we keep this file in a hex editor, some of the bytes say M1D1, which hints it might be a MIDI file. The bytes in the header that say M1D1 have to be changed to MThd as that is the file header for a MIDI file. After doing all these changes and then opening it in a software which can visualise MIDI files, we can see the flag.  
