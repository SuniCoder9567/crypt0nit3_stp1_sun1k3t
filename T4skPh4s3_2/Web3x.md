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
Well I have past exp with chals involving robots.txt. All I did was add /robots.txt to the URL directory which took me to a where it mentioned which file was disallowed.  

![Screenshot 2024-11-01 040257](https://github.com/user-attachments/assets/553de74d-5575-4e8f-989c-5e30704f272f)
So I ran the provided _.html_ files and guess what, the robots showed up.  


![Screenshot 2024-11-01 040317](https://github.com/user-attachments/assets/6fe948ea-ccb6-404f-bf62-efdd3385b994)


> FLAG -> picoCTF{ca1cu1at1ng_Mach1n3s_8028f}

# SQL Direct
