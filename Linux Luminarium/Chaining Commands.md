# CHAINIG WITH SEMICOLONS
For this chal, we have to chain `/challenge/pwn` and `/challenge/college` using the `;` symbol. Doing so will provide us with the flag.
```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn ; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{waAQvCshakl4uWSPRhcSCBG6QWt.dVTN4QDL3AjN1czW}
```
> FLAG -> pwn.college{waAQvCshakl4uWSPRhcSCBG6QWt.dVTN4QDL3AjN1czW}

# YOUR FIRST SHELL SCRIPT
For this chal, we need to create a shell script named `x.sh` and store the binaries `/challenge/pwn` and `/challenge/college` using the `;` symbol ot just with a nextline.
```
hacker@chaining~your-first-shell-script:~$ touch x.sh
hacker@chaining~your-first-shell-script:~$ nano x.sh


  GNU nano 4.8                                              x.sh
/challenge/pwn ; /challenge/college
```
After doing so, we need to run the new shell script using `bash`, which provides us with the flag.
```
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{cBvZ49hEB_-sTDAkr3DRiNh2CS0.dFzN4QDL3AjN1czW}
```
> FLAG -> pwn.college{cBvZ49hEB_-sTDAkr3DRiNh2CS0.dFzN4QDL3AjN1czW}

# REDIRECTING SCRIPT OUTPUT
For this chal, firstly we have to create a new shell script, here it is `flag.sh` and store the commands `/challenge/pwn` and `/challenge/college` in it.
```
nano flag.sh

  GNU nano 4.8                                            flag.sh

/challenge/pwn ; /challenge/college
```
After doing so, we pipe the output of the `flag.sh` script to `/challenge/solve` which provides us with the flag.
```
hacker@chaining~redirecting-script-output:~$ bash flag.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{UsMcYuMMcC9OEsDCBpt-GyGmRLK.dhTM5QDL3AjN1czW}
hacker@chaining~redirecting-script-output:~$
```
> FLAG -> pwn.college{UsMcYuMMcC9OEsDCBpt-GyGmRLK.dhTM5QDL3AjN1czW}

# EXECUTABLE SHELL SCRIPTS
For this chal, we have to create a new shell script. here it is `givemeflag.sh`. We need to write in `/challenge/solve` into it. After doing so, we need to make this file executable, and for that we need to use `chmod +x`. After that we provide the relative path of the shell script and execute it to get the flag.
```
hacker@chaining~executable-shell-scripts:~$ nano givemeflag.sh
hacker@chaining~executable-shell-scripts:~$ chmod +x givemeflag.sh
hacker@chaining~executable-shell-scripts:~$ ./givemeflag.sh
Congratulations on your shell script execution! Your flag:
pwn.college{QPY8btqvfjNwWlB5_PxzOrRTegv.dRzNyUDL3AjN1czW}
```
> FLAG -> pwn.college{QPY8btqvfjNwWlB5_PxzOrRTegv.dRzNyUDL3AjN1czW}
