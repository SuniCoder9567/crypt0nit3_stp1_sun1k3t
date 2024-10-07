# _cat_: NOT THE PET, BUT THE COMMAND!
For this chal, we will use the _cat_ command to display the contents of the _flag_ file present in the _~_ directory, which provides us with the flag.
```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{8JBj-MmYRrA9vPj40WNA5DDGoPp.dFzN1QDL3AjN1czW}
```
> FLAG -> pwn.college{8JBj-MmYRrA9vPj40WNA5DDGoPp.dFzN1QDL3AjN1czW}

# CATTING ABSOLUTE PATHS
For this chal, the _flag_ file is present in the _root(/)_ directory so we use _cat_ on it via providing the absolute path of the file i.e _cat /file_, which displays the content of the file and provides us with the flag.  
An alt way to do this would be to _cd_ to _root_ and simply do _cat flag_, this also provides us with the flag.
```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{kqlEQmzIzQlz5xMN9Fi5zWuXMG7.dlTM5QDL3AjN1czW}

ALT:-
hacker@commands~catting-absolute-paths:~$ cd /
hacker@commands~catting-absolute-paths:/$ cat flag
pwn.college{kqlEQmzIzQlz5xMN9Fi5zWuXMG7.dlTM5QDL3AjN1czW}

```
> FLAG -> pwn.college{kqlEQmzIzQlz5xMN9Fi5zWuXMG7.dlTM5QDL3AjN1czW}

# MORE CATTING PRACTICE
For this chal, the path to the flag file was given by the creator itself when we tried to use _cd_, the path to the flag file is _/usr/include/netrose/flag_. We do _cat /usr/include/netrose/flag_ which displays the content of the file and provides us with the flag.
```
hacker@commands~more-catting-practice:~$ cd
You used 'cd'! In this level, I don't allow you to change the working directory
--- you MUST chase pass 'cat' the absolute path of where I put it on the
filesystem (which is /usr/include/netrose/flag).
hacker@commands~more-catting-practice:~$ cat /usr/include/netrose/flag
pwn.college{gd9p45kMN2wns5L6OEpJwocWWya.dBjM5QDL3AjN1czW}
```
> FLAG -> pwn.college{gd9p45kMN2wns5L6OEpJwocWWya.dBjM5QDL3AjN1czW}

# GREPPING FOR A NEEDLE IN HAYSTACK
For this chal, we use the _grep_ command to search for the flag within the given file _data.txt_. We pass _grep "pwn.college" /challenge/data.txt_ to the shell which provides us with the flag.
```
grep "pwn.college" /challenge/data.txt
pwn.college{4AehqKeX8Lb-3f5oS6oLnb71HhK.ddTM4QDL3AjN1czW}
```
> FLAG -> pwn.college{4AehqKeX8Lb-3f5oS6oLnb71HhK.ddTM4QDL3AjN1czW}

# LISTING FILES
For this chal, we list the contents of challenge directory using _ls /challenge_ to find the executable file of _run_ renamed as _21851-renamed-run-27576_. We execute it and it provides us with the flag.
```
hacker@commands~listing-files:~$ ls /challenge
21851-renamed-run-27576  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/21851-renamed-run-27576
Yahaha, you found me! Here is your flag:
pwn.college{0b8ByXanOROw5gA5qDjMDiNH6-O.dhjM4QDL3AjN1czW}
```
> FLAG-> pwn.college{0b8ByXanOROw5gA5qDjMDiNH6-O.dhjM4QDL3AjN1czW}

# TOUCHING FILES
For this chal, we have to follow the instructions of the chal and create two files named _tmp/pwn_ and _tmp/college_ using _touch_ command. The we execute /challenge/run which provides us with the flag.
```
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{8MBKOjBaReUo72eE-AIqW1s52AJ.dBzM4QDL3AjN1czW}
```
> FLAG -> pwn.college{8MBKOjBaReUo72eE-AIqW1s52AJ.dBzM4QDL3AjN1czW}

# REMOVING FILES
For this chal, we have to remove a file named _delete_me_ from the home directory using the _rm_ command. Then we have to run _/challenge/check_ which checks wheteher the file is deleted or not. If deleted, it returns the flag.
```
hacker@commands~removing-files:~$ touch delete_me
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{cy_gza4DIQTPM2AD-FvLIj0Aigi.dZTOwUDL3AjN1czW}
```
> FLAG -> pwn.college{cy_gza4DIQTPM2AD-FvLIj0Aigi.dZTOwUDL3AjN1czW}

# HIDDEN FILES
For this chal, we have to run _ls / -a_ which lists the hidden files in the _root(/)_ directory. We seem to find this hidden file _.flag-995790357882_. We display its contents using _cat_ which provides us with the flag. 
```
hacker@commands~hidden-files:~$ ls / -a
.   .dockerenv          bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-995790357882  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:~$ cat /.flag-995790357882
pwn.college{oxwIJlXbVerREgjfGRwENsiLfeq.dBTN4QDL3AjN1czW}
```
> FLAG -> pwn.college{oxwIJlXbVerREgjfGRwENsiLfeq.dBTN4QDL3AjN1czW}

# AN EPIC FILESYSTEM QUEST
