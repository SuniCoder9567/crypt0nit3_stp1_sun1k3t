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

# IMPLICIT RELATIVE PATHS, FROM /  
For this chal, we had to change our _cwd_ to _root(/)_ and provide the relative path to the executable program i.e _challenge/run_, which provides us with the flag.
```
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{wqZLkfpNV_oZyaIAlyG87hOR4xH.dlDN1QDL3AjN1czW}
```
> FLAG -> pwn.college{wqZLkfpNV_oZyaIAlyG87hOR4xH.dlDN1QDL3AjN1czW}

# EXPLICIT RELATIVE PATHS, FROM /  
For this chal, we had to change our _cwd_ to _root(/)_ and provide an explicit relative path to the executable program i.e _./challenge/run_, which provides us with the flag. Using the . doesn't affect the absolute path, it refers to the same _cwd_ which is _root(/)_ here.
```
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{YBz9POFW6CjVZ70KAUB9KpZAC1C.dBTN1QDL3AjN1czW}

Alt :-
hacker@paths~explicit-relative-paths-from-:/$ ./././challenge/run
Correct!!!
./././challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{YBz9POFW6CjVZ70KAUB9KpZAC1C.dBTN1QDL3AjN1czW}
```
> FLAG -> pwn.college{YBz9POFW6CjVZ70KAUB9KpZAC1C.dBTN1QDL3AjN1czW}

# IMPLICIT RELATIVE PATH  
For this chal, we had to change our _cwd_ to _/challenge_, then we have to execute the executable program _run_ via providing an explicit relative path for doing so i.e _./run_ as Linux explicitly avoids automatically looking in the current directory when you provide a "naked" path.
```
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{kFY-T728ooCnnxNEHEWp27yJxZP.dFTN1QDL3AjN1czW}
hacker@paths~implicit-relative-path:/challenge$
```
> FLAG -> pwn.college{kFY-T728ooCnnxNEHEWp27yJxZP.dFTN1QDL3AjN1czW}

# HOME SWEET HOME
For this chal, we had to execute the _run_ program by providing the absolute path of _home/hacker/~_ aka _~/~(or any single character)_ as an argument to _/challenge/run_, where the contents of /challenge/run are copied to _~_ file in the _home/hacker_ or _~_ directory and displayed to provide us with the flag.
```
hacker@paths~home-sweet-home:~$ /challenge/run ~/~
Writing the file to /home/hacker/~!
... and reading it back to you:
pwn.college{E3AlGG7LUfrd_mUqxWSCvvonxKZ.dNzM4QDL3AjN1czW}
```
> FLAG -> pwn.college{E3AlGG7LUfrd_mUqxWSCvvonxKZ.dNzM4QDL3AjN1czW}
