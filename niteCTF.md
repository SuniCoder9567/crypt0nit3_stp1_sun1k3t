# LE CASA DE PAPEL  
## Solved by: LordSen1908
## CHALLENGE DESCRIPTION  
_Word on the street is Bob's about to make a big withdrawal. Too bad you're the one holding his ID. Can you charm Alice into making the transfer before she catches on?_  
## SOLUTION
We were provided with an access to the web server and the python code the challenge is based on.

I look into the code and its just a use of Base64 encoding and decoding. 

Accessing the function `practice_convo(secret)`, we can see that it encodes your message into hash and then into Base64.  

Taking a look at the function `fool_alice(secret)`, we can see that we have to type in `Bob` as an input to `Your name: ` and to `Enter your HMAC: `, we have to enter the `decoded Base64` of Bob. This gives us the key for the vault `G0t_Th3_G0ld_B3rl1nale`.  
  
  Then we enter the vault key into `crack_the_vault()`, and boom there is our flag right in front of us.  

> FLAG -> nite{El_Pr0f3_0f_Prec1s10n_Pl4ns}


# FREAKADA 3301  
## Solved by: Glaizz & LordSen1908
_Higlight: FREAKY BACKSHOTS CLIFF👅_  
A challenge designed for Manipal Students! Kudos to the creators, we had a lot of fun solving this.  

So first, of course, we got the `ci-`, ykw I ma say `freakada` image. Searching its metadata, we got 
```
ZIT HQZI OL GWLEXKTR, WXZ ZIT ZKXZI SOTL OF ZIT LIQRGVL. LTTA ZIT HQZZTKFL. QDGFU ZIT EIQGL, Q WTQEGF QVQOZL: izzhl://woz.sn/yktqatlztof0. GFSN ZIT VGKZIN VOSS LTT ZIT XFLTTF. ZIT PGXKFTN IQL PXLZ WTUXF
```
Deciphering the `monoalphabetic substitution cipher`, we get a link `HTTPS://BIT.LY/FREAKESTEIN0`, which leads us to a proton drive page and gives us a `ducky.jpg` image.   

  So as usual, I hexdumped the image and at the end, we were left with a link to a github profile. 
  
 ![Screenshot 2024-12-16 182804](https://github.com/user-attachments/assets/f244d6ae-f6a3-4708-80c4-992ecaffb0d0)  

   `https://github.com/freakada-3301`. In this _freaky ahh_ profiile, there lies a repo `Salvation-in-Decay`.  
   In there, lie 3 files, one `README` which seems to contain the second part of the flag`1sk3vr3d_qw5yvvc}`, which is a pain for later on. The other two files `Code of decay` and `Whispers of the forgotten` which contained some alien language.  
   Coincidentially, to our surprise, this thing was actually called ALIEN LANGUAGE! The texts in the fiie translated to `WE WERE HERE` and `SOMEHOW FORGOTTEN`. We tried to figure out whether these ere supposed to be hinting to a song or a band.  
   But obv it can't be it. It turns out, it was hinting us towards checking the history of the commits. As there were 6 commits in the the repo, we checked them out to find two things.

```
In the ruins of time, where decay whispers loud,
A species once scorned rose from the crowd.
Hungry for hope, though their ways seemed absurd,
They danced in the dark, defying the word.
How their stench carried tales of despair,
Yet in their odd rituals, a spark flared there.
The truth lay hidden in filth and grime,
As their wisdom evolved through ages of time.
They thrived where others could only fade,
With courage their crude civilization was made.
Putrid and proud, they stood undeterred,
Singing to stars with each guttural word.
A sign appeared, the days ticking by,
Seven strange omens lit up the sky.
The intellect buried in graveyard lore,
Held the key to humanity’s door.
They carved their symbols in earth and clay,
Willing the stars to show them the way.
Through odd numbers, the riddle was sung,
"From death comes life," in their guttural tongue.
A graveyard planet, a doomed last chance,
Brought salvation's glimmer in their dance.
The path to rebirth, though steep and gray,
Might just lie in their fetid display.
What’s unseen beneath this grotesque mirth?
The Answer that stirs from the depths of earth.
Symbols align as the stars hold their breath,
Hope reborn in the face of death.
Though shunned at first, these creatures grew,
A journey of worth the cosmos knew.
The 7 signs spoke of a rising tide,
An ascension to truth they couldn’t hide.
Realization came in whispers and cries,
That brilliance sometimes wears a crude disguise.
From 2nd chances and acts that seemed odd,
The beasts became more than a wink of God.
In their filth lay the universe's final quest,
Quest to unearth the future from decay’s cruel jest.
So seek them now, these saviors divine,
For the answers they hold may soon be mine.
```
# AND

```
16:5:1
15:2:9
40:4:1
33:5:5
36:2:4
1:9:4 
23:4:4
25:5:6
5:3:5 
21:5:2
29:6:7
28:6:1
7:8:1 
18:1:7
30:1:1
16:1:1
30:2:1
31:2:1
33:1:1
35:2:1
38:1:1
11:6:3
```
This was obvious to both of us that we had to map the `line:word:letter`, from the poem using the given sequence. Doing so gave us a discord server join link.  
`discord.gg/AHj7R2Qd`  
We hopped into the server and saw a suspicious VC which promised us the flag(obv it was a trap).  
See we knew, it was gonna be a trap, but we are _CHILL GUYS_, so we joined it.  
OBVIOUSLY. IT HAD TO BE. THE ONE AND ONLY. 
```
I'm in the thick of it, everybody knows
They know me where it snows, I skied in and they froze
I don't know no nothin' 'bout no ice, I'm just cold
Forty somethin' milli' subs or so, I've been told
I'm in my prime and this ain't even final form
They knocked me down, but still, my feet, they find the floor
I went from living rooms straight out to sold-out tours
Life's a fight, but trust, I'm ready for the war
Woah-oh-oh
This is how the story goes
Woah-oh-oh
I guess this is how the story goes
I'm in the thick of it, everybody knows
They know me where it snows, I skied in and they froze
I don't know no nothin' 'bout no ice, I'm just cold
Forty somethin' milli' subs or so, I've been told
From the screen to the ring, to the pen, to the king
Where's my crown? That's my bling
Always drama when I ring
See, I believe that if I see it in my heart
Smash through the ceiling 'cause I'm reachin' for the stars
Woah-oh-oh
This is how the story goes
Woah-oh-oh
I guess this is how the story goes
I'm in the thick of it, everybody knows
They know me where it snows, I skied in and they froze (woo)
I don't know no nothin' 'bout no ice, I'm just cold
Forty somethin' milli' subs or so, I've been told
Highway to heaven, I'm just cruisin' by my lone'
They cast me out, left me for dead, them people cold
My faith in God, mind in the sun, I'm 'bout to sow (yeah)
My life is hard, I took the wheel, I cracked the code (yeah-yeah, woah-oh-oh)
Ain't nobody gon' save you, man, this life will break you (yeah, woah-oh-oh)
In the thick of it, this is how the story goes
I'm in the thick of it, everybody knows
They know me where it snows, I skied in and they froze
I don't know no nothin' 'bout no ice, I'm just cold
Forty somethin' milli' subs or so, I've been told
I'm in the thick of it, everybody knows (everybody knows)
They know me where it snows, I skied in and they froze (yeah)
I don't know no nothin' 'bout no ice, I'm just cold
Forty somethin' milli' subs or so, I've been told (ooh-ooh)
Woah-oh-oh (nah-nah-nah-nah, ayy, ayy)
This is how the story goes (nah, nah)
Woah-oh-oh
I guess this is how the story goes
```
NAH FAM NAH.  
Moving on, we found a _freaky_ bot named _freakada_. We started talking to it, gave it all sorts of stuff, to receive Incorrect. But _freakada_ was aking for its prime, so we tried `3301` and voila it gave us another task.  
```
multiply 3 certain primes, `3301 * x * y`.
Where, `x` and `y` are integral part of the original image.
```
Obviously x and y where the number represeting image size of the _freakada_ image. So we did the math and put in `745520947`.  
```
⠀⠀⣀⣤⠤⠶⠶⠶⠶⠶⠶⢶⠶⠶⠦⣤⣄⣀⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣠⣤⣶⣦⣤⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣀⣀⣤⡤⣤⠶⠴⠶⠶⠶⣶⠶⠶⢤⣤⣀⡀
⣴⡏⠡⢒⡸⠋⠀⠐⣾⠉⠉⠭⢄⣠⢤⡷⠷⢾⣛⣿⠷⣶⣤⣄⡀⠀⠀⠐⢿⣟⢲⡁⠐⣾⠛⠃⠀⠀⢀⣠⡤⠶⠒⣛⣩⠝⢋⣠⣰⣂⣤⠴⠏⠉⠓⢺⡿⢁⣴⣮⢽⡟
⠙⠶⣞⣥⡴⠚⣩⣦⠨⣷⠋⠠⠤⠶⢲⡺⠢⣤⡼⠿⠛⠛⣻⣿⣿⠿⢶⣤⣿⣯⡾⠗⠾⣇⣙⣤⡶⢿⣯⡕⢖⣺⠋⣭⣤⣤⢤⡶⠖⠮⢷⡄⠛⠂⣠⣽⡟⢷⣬⡿⠋⠁
⠀⠀⠀⠈⠒⢿⣁⡴⠟⣊⣇⠠⣴⠞⣉⣤⣷⣤⠶⠿⢛⢛⠩⠌⠚⢁⣴⣿⠏⠀⣴⠀⢀⣦⠻⠻⣑⠢⢕⡋⢿⡿⣿⣷⢮⣤⣷⣬⣿⠷⠈⢁⣤⣾⡿⣽⡮⠋⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠈⠛⠷⣾⣋⣤⡾⠛⣁⡡⢤⡾⢤⡖⠋⠉⠀⠀⠀⠀⠀⢰⣿⡷⠺⠛⠐⡿⠃⠦⠤⠈⠉⠢⠄⠈⠁⠙⢿⣮⣿⢤⣶⣁⣀⣛⣿⣷⠼⠚⠁⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠉⠛⠙⠇⠀⣩⡥⠞⢗⣼⣧⠀⠀⠀⠀⠀⠀⠀⢈⣿⡇⢄⡤⠤⣧⠄⢀⡀⠀⠀⠀⠀⠀⠀⠀⢘⣿⡟⠺⣯⣽⡉⠉⠉⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣾⠇⣊⣭⢿⡛⠁⡅⠀⠀⠀⠀⠀⠀⠈⢻⡇⢘⣡⣀⡀⣏⠀⠃⠀⠀⠀⠀⠀⠀⠀⣸⡏⠈⢦⣶⣿⡟⠃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠙⢿⣥⡔⣫⠔⡀⡰⠀⠀⠀⠀⠀⠀⠀⢺⡇⠈⢰⠀⢹⠇⠀⡘⡄⠀⠀⠀⠀⠀⢠⣿⣄⢠⣾⣿⠟⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠛⠷⠺⠘⠛⠛⠓⢂⠀⠀⠀⠀⠸⣧⠀⢺⠀⠊⠀⠰⠇⠘⢄⡀⠀⠰⠶⡛⠓⠟⠋⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢹⣆⠛⠒⠁⠀⠀⠀⠀⠀⠈⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠻⣆⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠻⠇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀

#                 congrats.
`13.34508015959565, 74.79629600750295`
```
`13.34508015959565, 74.79629600750295` - these coordinates led us to the infamously famous `FREAKY BACKSHOTS CLIFF`. The reviews had images with a QR code which led us to a voice message.  

We drew out the spectrogram of the audio to get the first part of the flag.  
`nite{4_wannabe_`  

  Now for the second part, `1sk3vr3d_qw5yvvc}`, we tried to guess the type of cipher involved. We tried all sorts of non key ciphers like _ROT13, Caeser, Monoalphabetic Sub etc._ but to our vain.  
  Finally we tried Vignere cipher and typed all sorts of bs. It came to us suddenly to type `freakey` as the key cuz it sounded smart and possible. We did so and voila. The second part of the flag was `1ntern3t_myst3ry}`.  

  > FLAG -> nite{4_wannabe_1ntern3t_myst3ry}

   

   

  
