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

# Sum-O-Primes  
I tool some help from my friend Chat Gupta and generated this script which helps to find primes if both sum and product is given. 
```
from sympy import sqrt

def find_primes(sum_primes, product_primes):

    discriminant = sum_primes**2 - 4 * product_primes
    
    if discriminant < 0:
        raise ValueError("The given sum and product do not correspond to real numbers.")
    
    sqrt_discriminant = sqrt(discriminant)
    

    p = (sum_primes + sqrt_discriminant) // 2
    q = (sum_primes - sqrt_discriminant) // 2


    if not p.is_integer or not q.is_integer:
        raise ValueError("The calculated roots are not integers.")
    
    return int(p), int(q)

if __name__ == "__main__":

    sum_primes = 248878282147479407631683581202119202008113857267648242816387280016661770909433559540391540904735766035014251753170725650780440980606643804373951958290034800751257829018523044830468122826389084287622708715254713223303522388570617378324063310896161346186050183368553578353692887898281853413705176162420652556146
    product_primes = 14397774025004225993324435373479841323143935975053346165517984090132297018624689312592691344102355968341136940317334933016992680426294169407626539184359084321074000040939965885430451277187344911666759551422649486209938298125446066534891745094531222859443430894079142245216081256486936874280817564862769893645780979857446157952422613983118722910792157813441058095267855284014352295404885937555564838474289235824366704530230965338041116831007627876405345147820235814226436949637129018549397122198900007109231871447754296433655123133738574450189441923114132909194938534073968797793393952515066289029146527460197279861793
    
    p, q = find_primes(sum_primes, product_primes)
    print(f"The primes are: p = {p}, q = {q}")
```
With this script I get, 
```
p = 157413764743553826699637892824496494142257425519944914908812067385249036409707378886023684606076072660968006126733413007090111200661758134082388219463560702712200730607920598833853411695853957570596669597371949964585902561529632984740119495723922374899518139395431881164884447543164141550029690865864099833829
```
## &
```
 q = 91464517403925580932045688377622707865856431747703327907575212631412734499726180654367856298659693374046245626437312643690329779944885670291563738826474098039057098410602445996614711130535126717026039117882763258717619827040984393583943815172238971286532043973121697188808440355117711863675485296556552722317
```
With this, I just apply regular RSA logic for decryption by first calculating the euler's totient and then converting and from that calculating the private key. 
```
d = pow(e,-1,eu)
d
13347659435695588120854062895563036441556008331725836595791326416591665318226044044817342081474996438172367625659708539074315642837791703170715254607688861041785449753381898886142147615058234505670648794814927671905293516322195502761194710723842005390408540684370148853206485632549198524050225564007618756247945342255678804527913431472744359545517679458095852150775803615040170944607934451242319362198961810336019149081829332784211924296852351942634105253769419152169178598828518899938065050503923678805445899265124695624018984794454576312851134600951024585405664426565282397538763104550436729705164566287730816870001
```
From this i calculate the original message and convert it into its byte form.
```
>>> from Crypto.Util.number import long_to_bytes
>>> long_to_bytes(19023464378915228186961971911578673930414528675538075162786456500620236949484333128408678850102656856786656732489532083233175421) 
b'picoCTF{pl33z_n0_g1v3_c0ngru3nc3_0f_5qu4r35_92fe3557}'
```

> FLAG -> picoCTF{pl33z_n0_g1v3_c0ngru3nc3_0f_5qu4r35_92fe3557}
