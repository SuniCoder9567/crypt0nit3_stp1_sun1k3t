# MATCHING WITH *
For this chal, we had to _cd_ using globbing. We have to use the _*_ wildcard to change our directory to /challenge as it is restricted by the challenge to put in the whole path. We use _cd /ch*_ which tranfers us to _/challenge_ directory, we run our executable program using _/run_ and get our flag.
```
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{kfvZ4qc0Vqvqgqvjba4uX1OIBH2.dFjM4QDL3AjN1czW}
```

> FLAG -> pwn.college{kfvZ4qc0Vqvqgqvjba4uX1OIBH2.dFjM4QDL3AjN1czW}

# MATCHING WITH ?
For this chal, we had to _cd_ using globbing again but instead we use the single char wildcard _?_ to change our directory to _/challenge_, we only use the wildcard _?_ on _c_ and _l_ as specified in the chal itself. We use _cd /?ha??enge_ which tranfers us to _/challenge_ directory, we run our executable program using _/run_ and get our flag.
```
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{Y0E-HnXQeCIN3kgAPwRxLw-6rDj.dJjM4QDL3AjN1czW}
```
> FLAG -> pwn.college{Y0E-HnXQeCIN3kgAPwRxLw-6rDj.dJjM4QDL3AjN1czW}

# MATCHING WITH []
For this chal, we had to _cd_ to _/challenge/files_, then execute _challenge/run_ but along with the _[]_ wild card by passing _file__[bash] as per the chal itself. We run _/challenge/run file_[bash]_ which provides us with the flag.
```
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{Qp9IQkI_VTpjM1PMlJTBkKWufTO.dNjM4QDL3AjN1czW}
```
> FLAG -> pwn.college{Qp9IQkI_VTpjM1PMlJTBkKWufTO.dNjM4QDL3AjN1czW}

# MATCHING PATHS WITH []
For this chal, we had to execute _challenge/run_ from _~_ itself. We had to specify the path of the necessary files as an argument to _challenge/run_ by globbing the paths using _[]_ wildcard. We execute _/challenge/run /challenge/files/file_[bash]_ which provides us with the flag.
```
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{otQsP12AJCoQsWE95JumU8v-AH9.dRjM4QDL3AjN1czW}
hacker@globbing~matching-paths-with-:~$
```
> FLAG -> pwn.college{otQsP12AJCoQsWE95JumU8v-AH9.dRjM4QDL3AjN1czW}

# MIXING GLOBS
For this chal, we had to pull up to _/challenge/files_ using _cd_, then we had to write a glob which will match the files _"challenging", "educational", and "pwning"_. For this we have to pass the argument as _[cep]*_ , where c,e and p are the starting letters of the required files and _*_ wildcard, which the shell tries to replace with any file startinh with the specified letters. We pass _/challenge/files$ /challenge/run [cep]*_ to the shell which provides us with the flag.
```
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{04WAKwATZ7BhyKaX8VUNqJKusab.dVjM4QDL3AjN1czW}
```
> FLAG -> pwn.college{04WAKwATZ7BhyKaX8VUNqJKusab.dVjM4QDL3AjN1czW}

# Exclusionary Globbing
