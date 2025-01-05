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
I took some help from the internet and generated this script which helps to find primes if both sum and product is given. 
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
From this I calculate the original message and convert it into its byte form.
```
>>> from Crypto.Util.number import long_to_bytes
>>> long_to_bytes(19023464378915228186961971911578673930414528675538075162786456500620236949484333128408678850102656856786656732489532083233175421) 
b'picoCTF{pl33z_n0_g1v3_c0ngru3nc3_0f_5qu4r35_92fe3557}'
```

> FLAG -> picoCTF{pl33z_n0_g1v3_c0ngru3nc3_0f_5qu4r35_92fe3557}

# SRA
I have experienced a similar type of chal in cryptohack. I was given the value of c,d and e. From just c and d, we can calculate the value of p & q using an algorithm mentioned in _https://www.di-mgt.com.au/rsa_factorize_n.html_. 
I create my script based on this algorithm.
```
from sympy import divisors, isprime
from math import gcd

def find_primes(k, e):
   
    for pm1 in divisors(k):  
        p = pm1 + 1
        
        if isprime(p) and p.bit_length() == 128:
            for j in range(1, e):  
                if k % j != 0:  
                    continue
            
                q = (k // j // pm1) + 1
                if isprime(q) and q.bit_length() == 128:
                    print(f"Milgaya: p = {p}, q = {q}")
                    return p, q
    print("Nahi hai.")
    return None, None



k = 1725809408520309935408578378259035782206215788626506222040601783821068202817925200
e = 65537  
primes = find_primes(k, e)
    

```
I perform RSA functions on the received primes to get the following byte string and give it to the server which in turn gives me the flag.

![Screenshot 2024-12-27 193619](https://github.com/user-attachments/assets/7eb29b06-721f-46a5-bab7-7420e08a3818)
> FLAG -> picoCTF{7h053_51n5_4r3_n0_m0r3_38268294}

# No Padding, No Problem
Ahh another RSA question, broskie got that d and being choosy with that. How to break it and get my deserved flag.

THe chal suggests that there is no padding bruv. So any operation I bring about to the ciphertext can simply be undone by reversing the operation conducted on it.
```
>>> n = 90556814613262821398829014604100994702431944556933960677741278639382112195745686569482117165726584178226384814718635300051288976131278692841194040704194328670290115115317483510794294056611120006735175729884842144274739341339422363071916661904161475210606423132717410042545717927273134263506257294048538755669
>>> c = 64606267807405265029781016183996085179008292365231800870597196070757507179143952082638883739607645420900953671020759589237087966832375126811702013252499626839252193830386989418128287399849786943393703740279780724066016988959939750112280409507009609466751658362924812434109154492473859065722192474801393124185
>>> e
65537
>>> s = pow(2,e,n)
>>> s
38355497816291654050248373590848370174003189500674103473502225921993939013808783511868686374326940967511200341700302107616976934751813604581291584605707397927560691376577700580406570633939809419926007895302993813274076471948141978258566956090576945349209822551857342198281769626541148502887910739674902798785
>>> z = m*c
>>> z
2478005563805686431154127797467418208140993763107162228813410656675863982846639439527017204911742892485479601067163267030536372170558287089980437378000729479254509008516740818019864312951530852244609097483408887488363746115377876138131502837269714366825794338625481615597211314966617917722420166541387306084076499618116732161052794289659998587729832520503226894115978889152875296998449663882215823347543238102522397270111057710726642019495169417808531546459991211877258546844797650715795649572705372805725500698451966470137239777658407502396884473063785426259048553964412735792830832382509526524547929244511572115225
```
So I encrypt 2 using the generated value of n, and multiply it with the original ciphertext. Then I send in that ciphertext for decryption.
```
Give me ciphertext to decrypt: 2478005563805686431154127797467418208140993763107162228813410656675863982846639439527017204911742892485479601067163267030536372170558287089980437378000729479254509008516740818019864312951530852244609097483408887488363746115377876138131502837269714366825794338625481615597211314966617917722420166541387306084076499618116732161052794289659998587729832520503226894115978889152875296998449663882215823347543238102522397270111057710726642019495169417808531546459991211877258546844797650715795649572705372805725500698451966470137239777658407502396884473063785426259048553964412735792830832382509526524547929244511572115225
Here you go: 580550060391700078946913236734911770139931497702556153513487440893406629034802718534645538074938502890769425795379846471930
```
After I get the decrypted text, I simply `divide it by 2` which gives me the long form of the flag. I use the pookie function `long_to_bytes` to get the flag.
```
>>> j
290275030195850039473456618367455885069965748851278076756743720446703314517401359267322769037469251445384712897689923235965

>>> long_to_bytes(j)
b'picoCTF{m4yb3_Th0se_m3s54g3s_4r3_difurrent_5052620}'
>>>
```


> FLAG -> picoCTF{m4yb3_Th0se_m3s54g3s_4r3_difurrent_5052620}

# flag_printer
Whosoever put this chal in the TP, bro why ;-;.
So from what I understood reading the code is basically that the script begins by reading data from a file called `encoded.txt`. Each line of this file contains two integers x and y, which represent the coordinates of points on a curve. These points are stored as tuples (x, y) in the list points.  

Then it generates a Galois Field `GF` of size `MOD=7514777789`.  

For each point, a set of linear eqs is set up. The `y` seems to generate some sort of solution vector and for each x, a row is created in the matrix by calculating the powers of x modulo MOD. From what I discovered from the internet is that this is a Vandermonde Matrix.
`np.linalg.solve` seems to solve this set of linear equations whic generates the flag.  

But from the code itself and the given file `encoded.txt` which has `1769611` lines! It is clear that the code will take forever to run. (It's not like I did not try to tweak and run it and expected it to work fast smh).

I refered to the hint which gave generic form of a quadratic equation. From there, I deduced that the coefficients need to be analysed. The function hides in the points given. So, welcome back Engineering MAthematics 1. We bring back our old friend `INTERPOLATION`. The tried different forms of interpolation but still taking too long to run. I lost patience. I searched google for faster ways to interpolate and guess what just like fast-transpose, `fast-interpolation` exists too. I took help from random websites (even a writeup because till now I had arrived to the conclusion that I have to use fast-interpolation) and cooked up the script to solve the question.

```
from sage.all import GF, PolynomialRing
from math import ceil, log
import sys
sys.setrecursionlimit(1000000)

class Tree:
    def __init__(self, poly, X, left=None, right=None):
        self.left = left
        self.right = right
        self.poly = poly
        self.X = X

    def __len__(self):
        return len(self.X)

    def __mul__(self, other):
        return Tree(self.poly * other.poly, self.X + other.X, self, other)
    
    def __call__(self, *args, **kwargs):
        return self.poly(*args, **kwargs)

def comp_tree(X, R):
    if not X:
        return None
    
    if len(X) == 1:
        x = R.gen()
        return Tree(R(x - X[0]), [X[0]])

    x = R.gen()
    nodes = [Tree(R(x - xk), [xk]) for xk in X]
    
    while len(nodes) > 1:
        new_nodes = []
        for i in range(0, len(nodes) - 1, 2):
            new_nodes.append(nodes[i] * nodes[i + 1])
        if len(nodes) % 2:
            new_nodes.append(nodes[-1])
        nodes = new_nodes
    
    return nodes[0]

def fast_eval(f, tree):
    if tree is None:
        return []
    
    if len(tree.X) == 1:
        return [f(-tree.poly[0])]
    
    if f.degree() == 0:
        return [f] * len(tree.X)

    A = []
    B = []
    
    if tree.left:
        _, r1 = f.quo_rem(tree.left.poly)
        A = fast_eval(r1, tree.left)
    if tree.right:
        _, r2 = f.quo_rem(tree.right.poly)
        B = fast_eval(r2, tree.right)
        
    return A + B

def calc_weights(Y, tree):
    if tree is None or not Y:
        return []
    
    try:
        derivative = tree.poly.derivative()
        weights = fast_eval(derivative, tree)
        if not weights:
            return []
        return [y/w for y, w in zip(Y, weights) if w != 0]
    except Exception as e:
        print(f"Error in calc_weights: {e}")
        return []

def fast_interpolate_recursive(weights, tree):
    if tree is None or not weights:
        return 0
    
    if len(tree.X) == 1:
        if weights:
            return weights[0]
        return 0

    try:
        mid = len(tree.left.X) if tree.left else 0
        W1 = weights[:mid]
        W2 = weights[mid:]
        
        r0 = fast_interpolate_recursive(W1, tree.left) if tree.left else 0
        r1 = fast_interpolate_recursive(W2, tree.right) if tree.right else 0
        
        result = r0 * tree.right.poly if tree.right else 0
        result += r1 * tree.left.poly if tree.left else 0
        
        return result
    except Exception as e:
        print(f"Error in fast_interpolate_recursive: {e}")
        return 0

def get_coefficients(poly):
    coeffs = []
    for coeff in poly.coefficients(sparse=False)[:-1]:
        coeff_int = int(coeff)
        if coeff_int < 0:
            coeff_int = 256 + coeff_int
        coeffs.append(coeff_int % 256)
    return coeffs

def main():
    try:
        print("Reading input points...")
        X, Y = [], []
        with open('encoded.txt', 'r') as f:
            for line in f:
                x, y = map(int, line.strip().split())
                X.append(x)
                Y.append(y)

        print(f"Read {len(X)} points")

        MOD = 7514777789
        K = GF(MOD)
        R = PolynomialRing(K, 'x')
        
        print("Building computation tree...")
        tree = comp_tree(X, R)
        if tree is None:
            raise ValueError("Failed to build computation tree")
        
        print("Computing weights...")
        weights = calc_weights(Y, tree)
        if not weights:
            raise ValueError("Failed to compute weights")
        
        print("Performing fast interpolation...")
        result = fast_interpolate_recursive(weights, tree)
        if result == 0:
            raise ValueError("Interpolation failed")
        
        print("Processing coefficients...")
        coeffs = get_coefficients(result)
        
        print(f"Writing {len(coeffs)} bytes to output.bmp...")
        with open("output.bmp", "wb") as f:
            f.write(bytes(coeffs))
        
        print("Done!")
        
    except Exception as e:
        print(f"Error in main: {e}")
        sys.exit(1)

if __name__ == "__main__":
    main()
```
This generated the output.bmp which was corrupted and not opening. Even more frustration, I just put the image on my web browser and out of luck, there it was. The flag was in plain sight.  


![Screenshot 2024-12-30 170728](https://github.com/user-attachments/assets/50ad3947-63dd-4405-a97f-740cf4ecb36f)  
> FLAG -> picoctf{i_do_hope_you_used_the_favorite_algorithm_of_every_engineering_student}
