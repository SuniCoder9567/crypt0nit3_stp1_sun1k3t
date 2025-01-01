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
> FLAG -> pwn.college{ofkpZytt4JvcPhJ7ZWpWzrGI5iP.0lM1IDL3AjN1czW}
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

# LEVEL 2.1
So here is where things went a little out of pure simplicity.  
I had to disassemble the file using `Ghidra`.  
```
001014ae 0f b6 45 f2             MOVZX      EAX,byte ptr [RBP + local_16]       ; Load byte 0 ('a')
001014b2 88 45 f0                MOV        byte ptr [RBP + local_18],AL        ; Store byte 0 in `local_18`
001014b5 0f b6 45 f4             MOVZX      EAX,byte ptr [RBP + local_16+0x2]  ; Load byte 2 ('c')
001014b9 88 45 f1                MOV        byte ptr [RBP + local_17],AL        ; Store byte 2 in `local_17`
001014bc 0f b6 45 f1             MOVZX      EAX,byte ptr [RBP + local_17]       ; Load byte 2 ('c')
001014c0 88 45 f2                MOV        byte ptr [RBP + local_16],AL        ; Write 'c' to byte 0
001014c3 0f b6 45 f0             MOVZX      EAX,byte ptr [RBP + local_18]       ; Load byte 0 ('a')
001014c7 88 45 f4                MOV        byte ptr [RBP + local_16+0x2],AL    ; Write 'a' to byte 2

```
This function seems to mangle the 0th and 2nd index of the license key.
It was loading `xslgc` into the register which ig is the license key.  
I ran the program, have `lsxgc` as the license key and voila, FLAG milgaya.

> FLAG -> pwn.college{01dDzUy1UJurslFZpyEgyoJBDxw.0FN1IDL3AjN1czW}

# LEVEL 3.0
AS the previous `.0` chals, I ran the chal and it told be that the license key was mangled to be reverses and the expected outcome was given to me, so I converted them into ASCII.  
`jggov`was the translation which I provided as `voggj` thus I got the flag.  
```
voggj
Initial input:

        76 6f 67 67 6a

This challenge is now mangling your input using the `reverse` mangler.

This mangled your input, resulting in:

        6a 67 67 6f 76

The mangling is done! The resulting bytes will be used for the final comparison.

Final result of mangling input:

        6a 67 67 6f 76

Expected result:

        6a 67 67 6f 76

Checking the received license key!

You win! Here is your flag:
pwn.college{Et1sO0oNNfxxxxAWGD5xKiYN0eR.0VN1IDL3AjN1czW}
```
> FLAG -> pwn.college{Et1sO0oNNfxxxxAWGD5xKiYN0eR.0VN1IDL3AjN1czW}

# LEVEL 3.1
This chal tuurned out to be same as te previous one, simple reversal.  
I diassembled the code using `Ghidra`. 
```
                             LAB_001014b7                                    XREF[1]:     001014fd(j)  
        001014b7 8b 45 ec        MOV        EAX,dword ptr [RBP + local_1c]
        001014ba 48 98           CDQE
        001014bc 0f b6 44        MOVZX      EAX,byte ptr [RBP + RAX*0x1 + -0xe]
                 05 f2
        001014c1 88 45 ea        MOV        byte ptr [RBP + local_1e],AL
        001014c4 b8 04 00        MOV        EAX,0x4
                 00 00
        001014c9 2b 45 ec        SUB        EAX,dword ptr [RBP + local_1c]
        001014cc 48 98           CDQE
        001014ce 0f b6 44        MOVZX      EAX,byte ptr [RBP + RAX*0x1 + -0xe]
                 05 f2
        001014d3 88 45 eb        MOV        byte ptr [RBP + local_1d],AL
        001014d6 8b 45 ec        MOV        EAX,dword ptr [RBP + local_1c]
        001014d9 48 98           CDQE
        001014db 0f b6 55 eb     MOVZX      EDX,byte ptr [RBP + local_1d]
        001014df 88 54 05 f2     MOV        byte ptr [RBP + RAX*0x1 + -0xe],DL
        001014e3 b8 04 00        MOV        EAX,0x4
                 00 00
        001014e8 2b 45 ec        SUB        EAX,dword ptr [RBP + local_1c]
        001014eb 48 98           CDQE
        001014ed 0f b6 55 ea     MOVZX      EDX,byte ptr [RBP + local_1e]
        001014f1 88 54 05 f2     MOV        byte ptr [RBP + RAX*0x1 + -0xe],DL
        001014f5 83 45 ec 01     ADD        dword ptr [RBP + local_1c],0x1
```
After analyzing the function, it was just simple reversal. THe register had the value `qwzny`, so I gave the license key as `ynzwq`.
```
Ready to receive your license key!

ynzwq
Checking the received license key!

You win! Here is your flag:
pwn.college{cGpeRs2aD8yNgfqO-WwwavNSPWk.0lN1IDL3AjN1czW}
```
> FLAG -> pwn.college{cGpeRs2aD8yNgfqO-WwwavNSPWk.0lN1IDL3AjN1czW}
# LEVEL 4.0
This chal uses the sort mangler. As usual hex -> ASCII conversion.  
```
Expected result:

        62 6a 6d 71 76

Checking the received license key!

You win! Here is your flag:
pwn.college{AMy-My4dBPE6FjN9r7ti4beBdiI.01N1IDL3AjN1czW}
```
> FLAG -> pwn.college{AMy-My4dBPE6FjN9r7ti4beBdiI.01N1IDL3AjN1czW}

# LEVEL 4.1
This challenge was also the same as the prev one, to test my luck, isntead of `Ghidra` I ran `strings` on the challenge file.  
`hostz` is the stored register value and is already sorted. I give it, it gets verified. Ez pz
```
Ready to receive your license key!

hostz
Checking the received license key!

You win! Here is your flag:
pwn.college{cw3F-5YU-xNMMvLYqS17Gd1SweE.0FO1IDL3AjN1czW}
```
> FLAG -> pwn.college{cw3F-5YU-xNMMvLYqS17Gd1SweE.0FO1IDL3AjN1czW}

# LEVEL 5.0 



