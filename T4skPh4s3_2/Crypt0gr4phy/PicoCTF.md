# spelling-check  
So for this one, I analysed the python code and came to the conclusion that it was a random susbtitution cipher. So I went to one on the website I used during OASISCTF _https://www.boxentriq.com/code-breaking/cryptogram_. So, I just put in the encrypted text `brcfxba_vfr_mid_hosbrm_iprc_exa_hoav_vwcrm` and put it on _auto-solve_ which gave me the first result as `perhaps the dog jumped over was just tired` which was a proper plaintext making sense! So, using the long ol' method of trial and error, I enclosed the decrypted text in picoCTF{} and added the necessary underscores. And Voila!, the challenge was solved.  


![Screenshot 2024-11-10 161408](https://github.com/user-attachments/assets/fc70fef4-700f-4c57-b250-264de90f3c9e)  

_ps: the og message had don instead of dog, but in the next solve, it was dog. So in the second run, the flag was correct!_


> FLAG-> picoCTF{perhaps_the_dog_jumped_over_was_just_tired}

# Scrambled RSA
