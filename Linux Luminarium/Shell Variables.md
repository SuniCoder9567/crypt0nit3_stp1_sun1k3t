# PRINTING VARIABLES
For this chal, all we need to do is use _echo_ to print a variable. To do so, there must be _$_ character before the variable. Running _echo $FLAG_ will provide us with the flag.
```
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{8D6t6h7UHOL5k7YJ-fXRAc_7Wdz.ddTN1QDL3AjN1czW}
```
> FLAG-> pwn.college{8D6t6h7UHOL5k7YJ-fXRAc_7Wdz.ddTN1QDL3AjN1czW}

# SETTING VARIABLES
For this chal, all we need to do is set the value of the variable _PWN_ to _COLLEGE_, i.e _PWN=COLLEGE_, which provides us with the flag
```
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{8hRhW62iZS0N5BrmaM3zGUFaTWt.dlTN1QDL3AjN1czW}
```
> FLAG -> pwn.college{8hRhW62iZS0N5BrmaM3zGUFaTWt.dlTN1QDL3AjN1czW}

# MULTI-WORD VARIABLES
FOr this chal, we have to adhere to the rules of the BASH shell that we cannot assign a value to a variable in the linux shell with spaces alone, it will terminate variable assignment and interpret the word after the space as a command. To store values with spaces we must use _""_ to quote the value. Here we pass _PWN="COLLEGE YEAH"_
which provides us with the flag.
```
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{MD1ts12vesVFNErldPsYS4qzLAJ.dBjN1QDL3AjN1czW}
```
> FLAG -> pwn.college{MD1ts12vesVFNErldPsYS4qzLAJ.dBjN1QDL3AjN1czW}

# EXPORTING VARIABLES
For this chal, we have to set the value of _PWN_ variable as _COLLEGE_ and export it and set the value of _COLLEGE_ variable as _PWN_ but we don't export it. We open a child shell using _sh_ and run _/challenge/run_, which provides us with the flag.
```
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ sh
sh-5.2$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{0dI_zxNGWtfjHAM67DCoLSo9vjc.dJjN1QDL3AjN1czW}
```
> FLAG -> pwn.college{0dI_zxNGWtfjHAM67DCoLSo9vjc.dJjN1QDL3AjN1czW}

# PRINTING EXPORTED VARIABLES
For this chal, we had to use the _env_ command whihc literally prints out the contents of all the exported variables. Running the command printed out a whole lot of content, so I piped the output to the _grep_ command. Running _env | grep pwn.college_ provides us with the flag.
```
hacker@variables~printing-exported-variables:~$ env | grep pwn.college
FLAG=pwn.college{ANjI_0_mOOuB70iKzE1uilQJ3tz.dhTN1QDL3AjN1czW}
```
> FLAG -> pwn.college{ANjI_0_mOOuB70iKzE1uilQJ3tz.dhTN1QDL3AjN1czW}

# STORING COMMAND OUTPUT
For this challenge, we had to store the output after running _/challenge/run_ into the _PWN_ variable using _$()_. We had to run _PWN=$(/challenge/run)_ and then display the contents of the variable using _echo_ command. 
```
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{oiXc_DvhNHR2f_wIF5SC0wP4eja.dVzN0UDL3AjN1czW}
```
> FLAG -> pwn.college{oiXc_DvhNHR2f_wIF5SC0wP4eja.dVzN0UDL3AjN1czW}

# READING INPUT
For this chal, we have to take an input as _COLLEGE_ and store it into the _PWN_ variable, which is done using the _read_ command. We use the _-p_ argument, which lets us specify a prompt. Running _read -p "WANT FLAG? " PWN_ asks us for input and then we
provide _COLLEGE_ as the input which provides us with the flag.
```
hacker@variables~reading-input:~$ read -p "WANT FLAG? " PWN
WANT FLAG? COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{sUrK1kvXqLGMEaaNwOq10rGG5E5.dhzN1QDL3AjN1czW}
```
> FLAG -> pwn.college{sUrK1kvXqLGMEaaNwOq10rGG5E5.dhzN1QDL3AjN1czW}

# READING FILES
For this chal, we have to read the contents of _/challenge/read_me_ file as _stdin_ by redirecting it to the PWN variable using _<_. We run _read PWN < /challenge/read_me_ which provides us with the flag.
```
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{I_siJJC9uJEkYgcfPp7vYl7T18f.dBjM4QDL3AjN1czW}
```
> FLAG -> pwn.college{I_siJJC9uJEkYgcfPp7vYl7T18f.dBjM4QDL3AjN1czW}
