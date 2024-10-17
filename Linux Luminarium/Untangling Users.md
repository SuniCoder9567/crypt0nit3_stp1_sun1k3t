# BECOMING ROOT WITH SU
For this chal, first we use the "OLD IS GOLD" _su_ to login as the root user, with the provided password _hack-the-planet_. After logging in as the _root_ user, we _cat_ the _/flag_ file which provides us with the flag.
```
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{YoRENvoQfduZc1itHJ__ORGmXMg.dVTN0UDL3AjN1czW}
```
> FLAG -> pwn.college{YoRENvoQfduZc1itHJ__ORGmXMg.dVTN0UDL3AjN1czW}

# OTHER USERS WITH SU
For this chal, we use _su_ to login to another user _zardus_ by providing it as an argument to _su_. The we type in the given pwd _dont-hack-me_ and login as _zardus_. Then we run _/challenge/run_, whcih provides us with our flag.
```
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{k1_AAdKNyrO3tQ5IWvnq2aXT1ll.dZTN0UDL3AjN1czW}
```
> FLAG -> pwn.college{k1_AAdKNyrO3tQ5IWvnq2aXT1ll.dZTN0UDL3AjN1czW}

# CRACKING PASSWORDS
For this chal, we have to use the _JOHN THE RIPPER_tool to crack the password of the user _zardus_ from the leaked backup file _/challenge/shadow-leak_. AFter the we get the password, we login to _zardus_ and run _/challenge/run_ which provides us with the flag.
```
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04945g/s 287.9p/s 287.9c/s 287.9C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{AswkR0yXVm0XEQlOTMY41jfLbj1.ddTN0UDL3AjN1czW}
```
> FLAG -> pwn.college{AswkR0yXVm0XEQlOTMY41jfLbj1.ddTN0UDL3AjN1czW}

# USING SUDO
For this chal, all we have to do is run our command of _cat flag.txt_ along with _sudo_, which is the modern day's _su_! INstead of launching another shell using _su_, sudo itself gives commands to the shell as the _root_ user. 
```
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{AhVjnffXYPlz9ef-Z55L-vzP-_f.dhTN0UDL3AjN1czW}
```
> FLAG -> pwn.college{AhVjnffXYPlz9ef-Z55L-vzP-_f.dhTN0UDL3AjN1czW}
