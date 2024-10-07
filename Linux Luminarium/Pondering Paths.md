# THE ROOT  
For this chal, we have to provide the path _/pwn_ to invoke the program which provides us with the flag. _pwn_ is the executable program which is present in the root directory.
```
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{MEiHwPADvnKGFyW9eWM4aOnu2Og.dhzN5QDL3AjN1czW}

```
> FLAG -> pwn.college{MEiHwPADvnKGFyW9eWM4aOnu2Og.dhzN5QDL3AjN1czW}

# PROGRAM AND ABSOLUTE PATHS  
For this chal, we have to provide the path _/challenge/run_ to invoke the program which provides us with the flag. _challenge_ is a directory located in the root directory which contains the executable program _run_.
```
hacker@paths~program-and-absolute-paths:/$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{UlJaeNSDsI4kPN4ylzs2usXlG6O.dVDN1QDL3AjN1czW}

```
>FLAG -> pwn.college{UlJaeNSDsI4kPN4ylzs2usXlG6O.dVDN1QDL3AjN1czW}

# POSITION THY SELF  
For this chal, we have to go to the required directory _/usr/share/doc/fontconfig_ to execute the _/challenge/run_ program which provides us with the flag.
```
hacker@paths~position-thy-self:~$ ~
ssh-entrypoint: /home/hacker: Is a directory
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/doc/fontconfig directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /usr/share/doc/fontconfig
hacker@paths~position-thy-self:/usr/share/doc/fontconfig$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{Y6Gf83R59pUXZGo8nPoHuMgE8uw.dZDN1QDL3AjN1czW}
```
> FLAG -> pwn.college{Y6Gf83R59pUXZGo8nPoHuMgE8uw.dZDN1QDL3AjN1czW}

# POSITION ELSEWHERE  
For this chal, again we need to pull up to the req directory _/usr/share/build-essential_  to execute the _/challenge/run_ program which provides us with the flag.
```
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/build-essential directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /usr/share/build-essential
hacker@paths~position-elsewhere:/usr/share/build-essential$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{8UrIcmfcI2FXGEigaEwcU9G63uR.ddDN1QDL3AjN1czW}
```
> FLAG -> pwn.college{8UrIcmfcI2FXGEigaEwcU9G63uR.ddDN1QDL3AjN1czW}

# POSITION YET ELSEWHERE 
This chain of chals repeatedly making us do the same task is just to make us learn how to change directories using the **cd** command, we repeat the same task as the above two chals and get our flag.
```
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /etc directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /etc
hacker@paths~position-yet-elsewhere:/etc$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{UJuF-IJN2f2CEbEzasxs4IWKq90.dhDN1QDL3AjN1czW}
```
> FLAG -> pwn.college{UJuF-IJN2f2CEbEzasxs4IWKq90.dhDN1QDL3AjN1czW}


