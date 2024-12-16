# LE CASA DE PAPEL  
## CHALLENGE DESCRIPTION  
_Word on the street is Bob's about to make a big withdrawal. Too bad you're the one holding his ID. Can you charm Alice into making the transfer before she catches on?_  
## SOLUTION
We were provided with an access to the web server and the python code the challenge is based on.

I look into the code and its just a use of Base64 encoding and decoding. 

Accessing the function `practice_convo(secret)`, we can see that it encodes your message into hash and then into Base64.  

Taking a look at the function `fool_alice(secret)`, we can see that we have to type in `Bob` as an input to `Your name: ` and to `Enter your HMAC: `, we have to enter the `decoded Base64` of Bob. This gives us the key for the vault `G0t_Th3_G0ld_B3rl1nale`.  
  
  Then we enter the vault key into `crack_the_vault()`, and boom there is our flag right in front of us.  

> FLAG -> nite{El_Pr0f3_0f_Prec1s10n_Pl4ns}
  
