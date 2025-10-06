# description:
This floor feels like a digital world. The space is an illusion, all pink and sweet, stretching around you in impossible patterns. Here, you are no longer a climber but just another user.

Ahead, a door glows faintly. It is the only path forward and requires a level of authority you do not yet have. Fragments of session memory flicker, hinting at what it might take to gain higher access.
# writeup:
flag:```citadel{fru1tc4k3_4nd_c00k13s}```

In this challenge, they gave a website and when we open it, it tells that only admins can look at the secret message. I clicked on inspect page, went to cookies where there was a cookie called user with value user. I changed the value to admin, then refreshed the page and the flag was there. 
