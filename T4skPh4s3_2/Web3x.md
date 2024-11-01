# INSPECT HTML
For this chal, all we gotta do is pull up to the webbsite, inspect the HTML source file and _VOILA!_, there lies our flag in plain sight.


> ![Screenshot 2024-11-01 025551](https://github.com/user-attachments/assets/0349a19c-10c6-42a3-ba1f-86e94a1bc168)

> FLAG -> picoCTF{1n5p3t0r_0f_h7ml_8113f7e2}

# Intro to burp
Well I have had some experience with burpsuite from past chals. For this one though, we needed to click on register after proiding some random bs details and intercept the incoming request for 2FA. I simply changed the request method form `GET` to `POST` and voila the flag was in front of me.  


![Screenshot 2024-11-01 042710](https://github.com/user-attachments/assets/afd0cfb3-507b-4436-9ccd-9251bdd58807)


> FLAG -> picoCTF{#0TP_Bypvss_SuCc3$S_2e80f1fd}


# dont-use-client-side
Like the chal says, don't follow the client side man. All I did for this chal was inspecting the website and following a series of substrings given in order. These substrings were just derived from the original flag.  

![Screenshot 2024-11-01 035730](https://github.com/user-attachments/assets/73617819-0694-441b-88fc-8fabd478e619)  
So I manually mapped the substrings in order and formed the og flag.

> FLAG -> picoCTF{no_clients_plz_7723ce}

# Where are the robots
Well I have past exp with chals involving robots.txt. All I did was add /robots.txt to the URL directory which took me to a page where it mentioned which file was disallowed.  

![Screenshot 2024-11-01 040257](https://github.com/user-attachments/assets/553de74d-5575-4e8f-989c-5e30704f272f)
So I ran the provided _.html_ files and guess what, the robots showed up.  


![Screenshot 2024-11-01 040317](https://github.com/user-attachments/assets/6fe948ea-ccb6-404f-bf62-efdd3385b994)


> FLAG -> picoCTF{ca1cu1at1ng_Mach1n3s_8028f}

# SQL Direct
Nothing much, just a bunch of sql queries to seize the day!  
![Screenshot 2024-11-01 050526](https://github.com/user-attachments/assets/09baa2e0-2ef0-4595-8940-1f3c825f45e8)

> FLAG -> picoCTF{L3arN_S0m3_5qL_t0d4Y_21c94904}

# Who are you?

For this chal, we gotta go deep into step by step puzzle solving. 
```
Puzzle 1: Only people who use the official PicoBrowser are allowed on this site!
```
This indicates that I have to change my `User-Agent` to `PicoBrowser` , So I'ma `Burpsuite` this thing out.  

```
Puzzle 2: I don&#39;t trust users visiting from another site.
```
For this one, all we gotta do is add a Referer to our Requests and give it the same URL as the host website.

```
Puzzle 3: Sorry, this site only worked in 2018.
```
Well I guess this had smth to do with the date, so following the Format I set `Date` as `2018` and then...
```
Puzzle 4: I don&#39;t trust users who can be tracked.
```
After doing some online research, I concluded with that we have to set the value of DNT(Do Not Track) to `true or 1`
```
Puzzle 5: This website is only for people from Sweden.
```
After doing some research, I found out that we have to set the `X-Forwarded-For` header to a `Swedish IP Address`.
```
Puzzle 6: You&#39;re in Sweden but you don&#39;t speak Swedish?
```
This was kinda obv, I changed the accept language header to `sv-SE`, which is for the Svedish language.  
![Screenshot 2024-11-01 160619](https://github.com/user-attachments/assets/b39b326f-a685-4a3a-8ad9-917e17f929ae)


> FLAG -> picoCTF{http_h34d3rs_v3ry_c0Ol_much_w0w_b22d773c}
# Power Cookies
For this chal, all we had to do was inpect the website -> Go to Applications -> Get the Cookies -> A particulat cookie named `isAdmin` will have the value set as 0. We just have to set that as `isAdmin=1` and refresh the page, and voila we get the flag.  ![Screenshot 2024-11-01 161405](https://github.com/user-attachments/assets/fe75ca21-9c0d-446e-b8e2-667770e632d0)  
> FLAG -> picoCTF{gr4d3_A_c00k13_65fd1e1a}


# Most Cookies
I gotta admit that I underestimated this one. After doing thorough research on the internet and searching for tools by _dorking_ my ol' friend google, I found smth interesting which just may help me get the flag.  
_https://book.hacktricks.xyz/network-services-pentesting/pentesting-web/flask_.   
So I created a wordlist from the given harcoded set of cookies and ran the command  
```C:\Users\sunik>flask-unsign --wordlist C:\Users\sunik\OneDrive\Documents\Pictures\flagdedo.txt --unsign --cookie "eyJ2ZXJ5X2F1dGgiOiJibGFuayJ9.ZyTElw.H4uWq9gByrUrgshaHuqtamd6Gog" --no-literal-eval --threads 16```  
which gave me the secret key as `b'fortune'`.  
![Screenshot 2024-11-01 181531](https://github.com/user-attachments/assets/1be8c1c0-960e-488b-b818-8389b94db8ea)  
After this, I used another command to generate a new cookie which contains the necessary request i.e `{"very_auth":"admin}` using `C:\Users\sunik>flask-unsign --sign --cookie {'very_auth':'admin'} --secret 'fortune'` which gave me the new cookie as `eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.ZyTOmQ.KBIkUcdk2bRKSjPzJ1H3_aRCwJM`.  
Then, I simply submitted this cookie and damn g, the flag was right in front of us!  
![Screenshot 2024-11-01 183101](https://github.com/user-attachments/assets/5a35f853-4ce7-468c-b1d3-fab754d3fc2f)  




> FLAG -> picoCTF{pwn_4ll_th3_cook1E5_25bdb6f6}
