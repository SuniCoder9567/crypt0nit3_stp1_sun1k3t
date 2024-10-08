# LEARNING FROM DOCUMENTATION  
This chal exists to make us learn about how to pass arguments with commands accordingly to get what we want. Here, we are passing _--giveflag_ argument to the executable program _challenge/challenge_, which is necessary to execute the program and provide us with the flag.
```
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{4RZKLX-CvLGj-DOXkG4O6XxyqCG.dRjM5QDL3AjN1czW}
```
> FLAG -> pwn.college{4RZKLX-CvLGj-DOXkG4O6XxyqCG.dRjM5QDL3AjN1czW}

# LEARNING COMPLEX USAGE
For this chal, we had to read the Description.md file using the specified command _--printfile_ which displays its content. TO get the flag, first we locate where the flag is. I used _ls_ to find its loc and it was located at the _root(/)_ directory. We pass _/challenge/challenge --printfile /flag_ to the shell which provides us with the flag.

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
