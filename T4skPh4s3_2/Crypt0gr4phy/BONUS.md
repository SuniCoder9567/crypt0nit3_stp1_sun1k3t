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

# EFFICIENT EXCHANGE

