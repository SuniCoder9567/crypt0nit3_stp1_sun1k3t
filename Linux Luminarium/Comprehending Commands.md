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



