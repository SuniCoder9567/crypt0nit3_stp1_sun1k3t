# LEARNING FROM DOCUMENTATION  
This chal exists to make us learn about how to pass arguments with commands accordingly to get what we want. Here, we are passing _--giveflag_ argument to the executable program _challenge/challenge_, which is necessary to execute the program and provide us with the flag.
```
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{4RZKLX-CvLGj-DOXkG4O6XxyqCG.dRjM5QDL3AjN1czW}
```
> FLAG -> pwn.college{4RZKLX-CvLGj-DOXkG4O6XxyqCG.dRjM5QDL3AjN1czW}

# LEARNING COMPLEX USAGE
For this chal, we had to read the Description.md file using the specified argument _--printfile_ which displays its content. TO get the flag, first we locate where the flag is. I used _ls_ to find its loc and it was located in the _root(/)_ directory. We pass _/challenge/challenge --printfile /flag_ to the shell which provides us with the flag.

```
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /challenge/DESCRIPTION.md
Correct argument! Here is the /challenge/DESCRIPTION.md file:
While using most commands is straightforward, the usage of some commands can get quite complex.
For example, the arguments to commands like `sed` and `awk`, which we're definitely not getting into right now, are entire programs in an esoteric programming language!
Somewhere on the spectrum between `cd` and `awk` are commands that take arguments to their arguments...

This sounds crazy, but you've already encountered this with the `find` level in [Basic Commands](../commands).
`find` has a `-name` argument, and the `-name` argument itself takes an argument specifying the name to search for.
Many other commands are analogous.

Here is this level's documentation for `/challenge/challenge`:

> Welcome to the documentation for `/challenge/challenge`! This program allows you to print arbitrary files to the terminal, when given the `--printfile` argument. The argument to the `--printfile` argument is the path of the flag to read. For example, `/challenge/challenge --printfile /challenge/DESCRIPTION.md` will print out the description of the level!

Given that documentation, go get the flag!
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{4nRYfk5BpCEMu1JkTRBRqAMrK2Q.dVjM5QDL3AjN1czW}
```
> FLAG -> pwn.college{4nRYfk5BpCEMu1JkTRBRqAMrK2Q.dVjM5QDL3AjN1czW}

# READING MANUALS
First we read the man page of challenge, which shows us the following description.
```
hacker@man~reading-manuals:~$ man challenge

CHALLENGE(1)                                      Challenge Commands                                     CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --onmdem NUM
              print the flag if NUM is 431

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)
```
From this, we infer that we need to pass _/challenge/challenge_ with the argument _--onmdem 431_ to display the flag. So we pass _/challenge/challenge --onmdem 431_, which provides us with the flag.
```
hacker@man~reading-manuals:~$ /challenge/challenge --onmdem 431
Correct usage! Your flag: pwn.college{onm-BdGDPPeQmKdHO__yi-Ympy-.dRTM4QDL3AjN1czW}
```
> FLAG -> pwn.college{onm-BdGDPPeQmKdHO__yi-Ympy-.dRTM4QDL3AjN1czW}

# SEARCHING MANUALS
For this chal, we learn how to search man pages. We use _/randomtext_ to search in man pages and we can hit _n_ to go forwards for the same word and _N_ to go backwards. For this chal, I opened the man page of _challenge_, searched _/flag_ and hit _n_ until I found this _--evju This argument will give you the flag!_.

```
 --vhrjb
              A neat argument, but not the right one.

       --evju This argument will give you the flag!

       --sxbrs
              A neat argument, but not the right one.
```
So, I ran the argument _--evju_ along with _/challenge/challenge_, which provides us with the flag.
```
hacker@man~searching-manuals:~$ /challenge/challenge --evju
Initializing...
Correct usage! Your flag: pwn.college{gweqtzwYaxv1sayXDrbQrJszI7O.dVTM4QDL3AjN1czW}
```
> FLAG -> pwn.college{gweqtzwYaxv1sayXDrbQrJszI7O.dVTM4QDL3AjN1czW}

# SEARCHING MANUALS
For this chal, as specified by the chal, I ran _man man_ to know how to use man to search for a hidden manpage.
```
hacker@man~searching-for-manuals:~$ man -k challenge
bqyvtfrpvw (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man bqyvtfrpvw

CHALLENGE(1)                                      Challenge Commands                                     CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --bqyvtf NUM
              print the flag if NUM is 036

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)
```
