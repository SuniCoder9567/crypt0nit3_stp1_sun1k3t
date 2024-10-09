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
For this chal, as specified by the chal, I ran _man man_ to know how to use man to search for a hidden manpage. From the series of arguments listed, I found out a unique one which goes like  _man -k printf. Search the short descriptions and manual page names for the keyword printf as regular expression. Print out any matches._ So basically it checks the description of files too which contain the matching characters. I ran _man -k challenge_ which gave me the file I was searcing for.
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
So I used the argument specified in the aliased page and ran _/challenge/challenge --bqyvtf 036_, which provides us witht he flag.
```
hacker@man~searching-for-manuals:~$ /challenge/challenge --bqyvtf 036
Correct usage! Your flag: pwn.college{INbEq0y3MGPvtCSZfM6r099pvwF.dZTM4QDL3AjN1czW}
```
> FLAG -> pwn.college{INbEq0y3MGPvtCSZfM6r099pvwF.dZTM4QDL3AjN1czW}

# HELPFUL PROGRAMS
So for this chal, all we have to do us run _--help_ or _-h_ on _/challenge/challenge_ to know how to run it, it display the following contents:-
```
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
```
So I run _/challenge/challenge -p_ which gives me the secret value _491_ to get the flag.
```
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 491
```
Then I run _challenge/challenge -g 491_, which provides us with the flag.
```
hacker@man~helpful-programs:~$ /challenge/challenge -g 491
Correct usage! Your flag: pwn.college{g4F_z9t1SKJyhd7tRaOjcIQilDX.ddjM4QDL3AjN1czW}
```
> FLAG -> pwn.college{g4F_z9t1SKJyhd7tRaOjcIQilDX.ddjM4QDL3AjN1czW}

# HELP FOR BUILTINS

For this challenge, first I used the built in help command to get the whole list of builtin commands present in the shell
```
hacker@man~help-for-builtins:~$ help
GNU bash, version 5.2.32(1)-release (x86_64-pc-linux-gnu)
These shell commands are defined internally.  Type `help' to see this list.
Type `help name' to find out more about the function `name'.
Use `info bash' to find out more about the shell in general.
Use `man -k' or `info' to find out more about commands not in this list.

A star (*) next to a name means that the command is disabled.

 job_spec [&]                                                history [-c] [-d offset] [n] or history -anrw [filename]>
 (( expression ))                                            if COMMANDS; then COMMANDS; [ elif COMMANDS; then COMMAN>
 . filename [arguments]                                      jobs [-lnprs] [jobspec ...] or jobs -x command [args]
 :                                                           kill [-s sigspec | -n signum | -sigspec] pid | jobspec .>
 [ arg... ]                                                  let arg [arg ...]
 [[ expression ]]                                            local [option] name[=value] ...
 alias [-p] [name[=value] ... ]                              logout [n]
 bg [job_spec ...]                                           mapfile [-d delim] [-n count] [-O origin] [-s count] [-t>
 bind [-lpsvPSVX] [-m keymap] [-f filename] [-q name] [-u >  popd [-n] [+N | -N]
 break [n]                                                   printf [-v var] format [arguments]
 builtin [shell-builtin [arg ...]]                           pushd [-n] [+N | -N | dir]
 caller [expr]                                               pwd [-LP]
 case WORD in [PATTERN [| PATTERN]...) COMMANDS ;;]... esa>  read [-ers] [-a array] [-d delim] [-i text] [-n nchars] >
 cd [-L|[-P [-e]] [-@]] [dir]                                readarray [-d delim] [-n count] [-O origin] [-s count] [>
 challenge [--fortune] [--version] [--secret SECRET]         readonly [-aAf] [name[=value] ...] or readonly -p
 etc.
```
There I noticed the builtin command challenge. So I ran _help challenge_ which gave me this.
```
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "I5uPhdm4"
```
So considering the secret value _I5uPhdm4_, I ran it as an argument with _challenge_ as _challenge --secret I5uPhdm4_, which provides us with the flag.
```
hacker@man~help-for-builtins:~$ challenge --secret I5uPhdm4
Correct! Here is your flag!
pwn.college{I5uPhdm4SHZd6T8FToYFoRRl41F.dRTM5QDL3AjN1czW}
```
> FLAG -> pwn.college{I5uPhdm4SHZd6T8FToYFoRRl41F.dRTM5QDL3AjN1czW}
