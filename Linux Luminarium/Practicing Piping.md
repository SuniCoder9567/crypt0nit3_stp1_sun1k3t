# REDIRECTING OUTPUT
For this chal, we need to redirect the word _PWN_ into the _COLLEGE_ file using the _echo_ command and the _>_character. This provides us with the flag.
```
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{QowwSDdOkTIOlxXccuQu0hAVSdH.dRjN1QDL3AjN1czW}
```
> FLAG -> pwn.college{QowwSDdOkTIOlxXccuQu0hAVSdH.dRjN1QDL3AjN1czW}

# REDIRECTING MORE OUTPUT
For this chal, first we need to redirect the contents of /challenge/run into a new file named myflag. Doing so gives us this output.
```
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
```
After it confirms that the requirement has been satisfied, we _cat_ the file and thus get our flag.
```
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{4yYhJThEZaRPg3JZiFTpXdYp2ha.dVjN1QDL3AjN1czW}
```
> FLAG -> pwn.college{4yYhJThEZaRPg3JZiFTpXdYp2ha.dVjN1QDL3AjN1czW}

# APPENDING OUTPUT
For this chal, we have to the append the contents of _challenge/run_ to _~/the-flag_ using _>>_ character, it ensures that the data gets redirected into the old file itself without creating a new one. The following output is displayed.
```
WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
```
After getting the confirmation, I ran _cat_ on _the-flag_ which provides us with the flag.
```
hacker@piping~appending-output:~$ cat the-flag
 |
\|/ This is the first half:
 v
pwn.college{IM3yH1KxlAJbeWdq9j2izb04Y_r.ddDM5QDL3AjN1czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>)
rather than *append* mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!
```
> FLAG -> pwn.college{IM3yH1KxlAJbeWdq9j2izb04Y_r.ddDM5QDL3AjN1czW}

# REDIRECTING ERRORS
For this chal, we had to redirect the contents of _/challenge/run_ to the  _~/myflag_ file and redirect any rising errors to the _instructions_ file. After we execute this, we use _cat myflag_ which gives us the flag.
```
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{QnVsOplMgKR06gE5C-bLifGCDeX.ddjN1QDL3AjN1czW}
```
> FLAG -> pwn.college{QnVsOplMgKR06gE5C-bLifGCDeX.ddjN1QDL3AjN1czW}
