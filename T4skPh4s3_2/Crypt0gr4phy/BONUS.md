# CRYPTOHACK : ECC

## POINT ADDITION
Just followed the algorithm given.  
Due to this being in a finite field, the calculations are done using modulo `p` where `p=9739`.  
Substituting the values of P,Q and R, we get the flag.

```
def modularinv(value, p):
    return pow(value, -1, p)

def p_add(P, Q, a, p):
    if P == "O":
        return Q
    if Q == "O":
        return P

    x1, y1 = P
    x2, y2 = Q

    if x1 == x2 and (y1 + y2) % p == 0:
        return "O"

    if P != Q:
        numerator = (y2 - y1) % p
        denominator = modularinv((x2 - x1) % p, p)
        lam = (numerator * denominator) % p
    else:
        numerator = (3 * x1**2 + a) % p
        denominator = modularinv((2 * y1) % p, p)
        lam = (numerator * denominator) % p

    x3 = (lam**2 - x1 - x2) % p
    y3 = (lam * (x1 - x3) - y1) % p

    return (x3, y3)

a = 497
p = 9739
P = (493, 5564)
Q = (1539, 4742)
R = (4403, 5202)
res = p_add(P, P, a, p)
res = p_add(res, Q, a, p)
res = p_add(res, R, a, p)
    
print(res)
```
> FLAG -> crypto{4215,2162}

## EFFICIENT EXCHANGE

So we gotta calculate the shared secret but only the x coordinate from Alice is given `(815,3190)`.  
We are not given the y coordinate but we are given a set of hints from which we can derive the y coordinate.  
THe first thought that struck my mind was obviously to pu the value of x in the `Weierstrass equation` to get `y^2` out of it.  
Now to derive why from it, we are give the hint that the relation `p≡3mod4` is gonna help us calculate y from y^2.  
So, first let us calculate the two possible value of y.  
I wrote the block for that.
```
def sqrt(ysq, p):
    for i in range(1, p):
        if pow(i, 2) % p == ysq: #we need to consider with regard of %p as we are working with a finite field
            return (i, p - i)
```
So implementing this I found the two possible values of y to be `3452 & 6287`.  
Now to decide which is the correct one, we will use the hint they gave us (listed above).  
We need to check if `y % 4 == 3` in each case. The value of `y` which satisfies the case will be treated as the y component of Alice's public key.  
We find out that y2 aka `p-i` satisfies the relation, therefore satisfies the y component.  
We calculate the shared secret and give the x component to `decrypt.py` along with iv and ctext and just like that, we get aour flag.

> FLAG -> crypto{3ff1c1ent_k3y_3xch4ng3}

# FLIPPY - MetaCTF
