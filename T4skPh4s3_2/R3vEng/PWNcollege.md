# Level 1.0
For this chal, I first run the chal and type in gibberish to see what the program does. Surprisingly, broskies gave us the expected ouput right there in the errogenous output.  

I converted the given code ` 61 6a 7a 6e 68` into ASCII which turned out to be `ajznh`.  
Running it gave me the flag.  
```
ajznh
Initial input:

        61 6a 7a 6e 68

The mangling is done! The resulting bytes will be used for the final comparison.

Final result of mangling input:

        61 6a 7a 6e 68

Expected result:

        61 6a 7a 6e 68

Checking the received license key!

You win! Here is your flag:
pwn.college{QbMfLNEkK-qjjQE_iA_cmkWB2Yg.0VM1IDL3AjN1czW}
```
> FLAG -> pwn.college{QbMfLNEkK-qjjQE_iA_cmkWB2Yg.0VM1IDL3AjN1czW}

# Level 1.1
Well for this one, it was the same as the previous one but just with a lil twist. This time, no expected outcome was shown.  
So I ran `strings` for the challenge hoping I would find smth similar to the prev license key.  
Turns out I found `kwlpg` which seemed like it could be the license key. No problem in trying.  
I put it in, I get the flag.
```
Ready to receive your license key!

kwlpg
Checking the received license key!

You win! Here is your flag:
pwn.college{ofkpZytt4JvcPhJ7ZWpWzrGI5iP.0lM1IDL3AjN1czW}
```
# Level 2.0
For this chal, I did the same as I was doing for Level 1.0, I ran the challenge file and expected it so provide me with some sort of information about the expected outcome.  
And it did.  
It turns out the indexes `2 and 4 were swapped`.  
So I convert the expected outcome into ASCII, `mdtkq` but I provide the license key as `mdqkt` so that when the swapping occurs, `mdtkq` is received as the license key.
```
mdqkt
Initial input:

        6d 64 71 6b 74

This challenge is now mangling your input using the `swap` mangler for indexes `2` and `4`.

This mangled your input, resulting in:

        6d 64 74 6b 71

The mangling is done! The resulting bytes will be used for the final comparison.

Final result of mangling input:

        6d 64 74 6b 71

Expected result:

        6d 64 74 6b 71

Checking the received license key!

You win! Here is your flag:
pwn.college{QlD1vMHbxstD93QV-BWdUIzQTHk.01M1IDL3AjN1czW}
```

> FLAG -> pwn.college{ofkpZytt4JvcPhJ7ZWpWzrGI5iP.0lM1IDL3AjN1czW}
