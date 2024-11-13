# spelling-check  
So for this one, I analysed the python code and came to the conclusion that it was a random susbtitution cipher. So I went to one on the website I used during OASISCTF _https://www.boxentriq.com/code-breaking/cryptogram_. So, I just put in the encrypted text `brcfxba_vfr_mid_hosbrm_iprc_exa_hoav_vwcrm` and put it on _auto-solve_ which gave me the first result as `perhaps the dog jumped over was just tired` which was a proper plaintext making sense! So, using the long ol' method of trial and error, I enclosed the decrypted text in picoCTF{} and added the necessary underscores. And Voila!, the challenge was solved.  

  ![Screenshot 2024-11-10 161408](https://github.com/user-attachments/assets/fc70fef4-700f-4c57-b250-264de90f3c9e)  


_ps: the og message had don instead of dog, but in the next solve, it was dog. So in the second run, the flag was correct!_


> FLAG-> picoCTF{perhaps_the_dog_jumped_over_was_just_tired}

# Scrambled RSA
In this chal, basically whenever we send a string, it encrypts them and displays in a scrambled form. For example, when we put in `abc`, it might show for `c` then `a` and then `b`.  

So, here we write a script which gets us our flag.
```
from pwn import *
import string

r = remote("mercury.picoctf.net", 58251)
r.recvuntil(b"flag: ")
flagre = r.recvline().decode()
r.recvlines(2)

def encrypt(data: str):
    r.sendlineafter(b"I will encrypt whatever you give me: ", data.encode())
    r.recvuntil(b"Here you go: ")
    return r.recvline().decode().strip()

def get_unique_enc(prefix, char, seen):
    enc = encrypt(prefix + char)
    for seene in seen:
        enc = enc.replace(seene, "")
    return enc

known = "picoCTF{"
flag = ""

cipher_map = {}

for char in known:
    enc = get_unique_enc(flag, char, cipher_map)
    assert enc in flagre
    cipher_map[enc] = char
    flag += char
    flagre = flagre.replace(enc, "")

chars = "_}" + string.digits + string.ascii_letters

while not flag.endswith("}"):
    for char in chars:
        enc = get_unique_enc(flag, char, cipher_map)
        if enc not in flagre:
            continue
        cipher_map[enc] = char
        flag += char
        flagre = flagre.replace(enc, "")
        print(flag)
        break

```
So what this script does basically is, that it starts with a known part of the flag i.e `picoCTF{` and iteratively guesses the remaining characters. It tries to send character by character to the server and receives an encrypted result which it tries to match with the given encrypted flag to find a pattern. If there is a match, it adds the character to the `flag` plaintext. This process continues till we get the whole flag.  


![Screenshot 2024-11-14 013706](https://github.com/user-attachments/assets/355133f7-3284-49de-8b90-4fb519f03e2b)

> FLAG -> picoCTF{bad_1d3a5_1314164}
