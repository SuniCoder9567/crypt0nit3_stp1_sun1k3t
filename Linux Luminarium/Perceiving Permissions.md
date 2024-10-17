# CHANGING FILE OWNERSHIP
For this chal, we habe to change the ownership of _flag_ from _root_ to _hacker_. We use the _chown_ command to do so and then _cat_ the flag file which provides us with the flag.
```
hacker@permissions~changing-file-ownership:~$ cd /
hacker@permissions~changing-file-ownership:/$ chown hacker flag
hacker@permissions~changing-file-ownership:/$ cat flag
pwn.college{kBn4c2aOao561Sq8uulEdrc9i4i.dFTM2QDL3AjN1czW}
```
> FLAG -> pwn.college{kBn4c2aOao561Sq8uulEdrc9i4i.dFTM2QDL3AjN1czW}

# GROUPS AND FILES
For this chal, we have to change the group ownership of the flag file from _root_ to _hacker_ using the _chgrp_ command. The we cat the _/flag_ file which provides us with the flag.
```
After listing out the files from the root directory :-

-r--r-----    1 root root   58 Oct 17 10:50 flag
```
```
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{UcPMQ9B2v0Zri7uk4YVi6ZNrcfX.dFzNyUDL3AjN1czW}
```
> FLAG -> pwn.college{UcPMQ9B2v0Zri7uk4YVi6ZNrcfX.dFzNyUDL3AjN1czW}

# FUN WITH GROUP NAMES
For this chal, we use _id_ to fighure out which group is the user _hacker_ which turns out to be _grp12392_. Then we change the group ownership of _/flag_ from _root_ to _grp12392_. The we simply cat _/flag_ which provides us with the flag.
```
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp12392) groups=1000(grp12392)
hacker@permissions~fun-with-groups-names:~$ chgrp grp12392 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{Mu5y4Bd1-zacOWjGDifA28PvNYA.dJzNyUDL3AjN1czW}
```
> FLAG -> pwn.college{Mu5y4Bd1-zacOWjGDifA28PvNYA.dJzNyUDL3AjN1czW}

# CHANGING PERMISSIONS
For this chal, we had to make the file readable to other users. SO we use _chmod o+r /flag_ to make it readable to other users and then we _cat_ the _/flag_ file to get the flag.
```
hacker@permissions~changing-permissions:~$ ls -l / | grep flag
-r--------    1 root root   58 Oct 17 11:34 flag
hacker@permissions~changing-permissions:~$ chmod o+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{gAjIGs_v_UJ3GKAyNKAPp2NNa3t.dNzNyUDL3AjN1czW}
```
> FLAG -> pwn.college{gAjIGs_v_UJ3GKAyNKAPp2NNa3t.dNzNyUDL3AjN1czW}

# EXECUTABLE FILES
For this chal, we had to change make the file executable to _hacker_, so we use _chmod a+x /challenge/run_ which provides the permission to execute _/challenge/run_ to anyone who has the file. Running _/challenge/run_ gives us or flag.
```
hacker@permissions~executable-files:~$ chmod a+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{Un9Ld_tKuM4dKETlmJ9N2ewnY4O.dJTM2QDL3AjN1czW}
```
> FLAG -> pwn.college{Un9Ld_tKuM4dKETlmJ9N2ewnY4O.dJTM2QDL3AjN1czW}

# PERMISSION TWEAKING PRACTICE
For this chal, there are 8 rounds of permission tweaking were we have to carefully observe and change the permissions of _/challenge/pwn_ to get the flag.  
The following are the commands I put in to clear the Round of 8.
```
chmod g+wx /challenge/pwn
chmod g-w /challenge/pwn
chmod g-rx,o-r /challenge/pwn
chmod g+rx,o+rx /challenge/pwn
chmod u+x,g+rwx /challenge/pwn
chmod o+w /challenge/pwn
chmod u-rx,g-rx /challenge/pwn
chmod g-w,o-wx /challenge/pwn
```
After getting the ownership of _/flag_ file changes, we need to change its permissions to readable so we use _chmod a+r /flag_ and _cat_ it, which provides us with the flag.
```
hacker@permissions~permission-tweaking-practice:~$ chmod a+r /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{cfRKdC45-PlnpA4yJ3W8oVJQ6gg.dBTM2QDL3AjN1czW}
```
> FLAG -> pwn.college{cfRKdC45-PlnpA4yJ3W8oVJQ6gg.dBTM2QDL3AjN1czW}

# PERMISSION SETTING PRACTICE
For this chal, there are 8 rounds of permission setting were we have to carefully observe and change the permissions of _/challenge/pwn_ to get the flag.  
The following are the commands I put in to clear the Round of 8.
```
chmod u=rwx,g=rx,o=rx /challenge/pwn
chmod u=w,g=w,o=- /challenge/pwn
chmod u=x,g=rw,o=x /challenge/pwn
chmod u=x,g=-,o=rw /challenge/pwn
chmod u=-,g=rw,o=rw /challenge/pwn
chmod u=r,g=wx,o=rw /challenge/pwn
chmod u=-,g=r,o=w /challenge/pwn
chmod u=wx,g=r,o=rwx /challenge/pwn
```

After getting the ownership of _/flag_ file changes, we need to change its permissions to readable so we use _chmod a+r /flag_ and _cat_ it, which provides us with the flag.
```
hacker@permissions~permissions-setting-practice:~$ chmod u=r,g=r,o=r /flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{cHMyD8qCkgS5z2v3HSnfhlqHvW9.dNTM5QDL3AjN1czW}
```
> FLAG -> pwn.college{cHMyD8qCkgS5z2v3HSnfhlqHvW9.dNTM5QDL3AjN1czW}

# THE SUID BIT
For this chal, first we as the _s_ bit to the _/challenge/getroot_ to give it SUID permissions i.e the file can only be run by the owner user. After using _chmod u+s /challenge/getroot_, we get access to the root user and we can _cat_ the flag ourselves to get the flag.
```
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root!
Here is your shell...
root@permissions~the-suid-bit:~# cat /flag
pwn.college{kaOacwSI6orXFJMeR984t_qPxy8.dNTM2QDL3AjN1czW}
```
> FLAG -> pwn.college{kaOacwSI6orXFJMeR984t_qPxy8.dNTM2QDL3AjN1czW}
