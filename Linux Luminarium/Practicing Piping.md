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

# REDIRECTING INPUTS
For this chal, we have to store _COLLEGE_ in the _PWN_ file. For that, we do simple _stdout_ direction.
```
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN

```
After that, I redirect the input of _PWN_ file to _/challenge/run_ which provides us with the flag.
```
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{URo5GsBRoVbCh9wOavD3yVMgAIV.dBzN1QDL3AjN1czW}
```
> FLAG -> pwn.college{URo5GsBRoVbCh9wOavD3yVMgAIV.dBzN1QDL3AjN1czW}

# GREPPING STORED RESULTS
In this chal, we have to redirect the contents of _/challenge/run_ to _/tmp/data.txt_ using _>_.
```
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
```
After doing so we run the _grep_ command with to be searched as _pwn.college_ and file as _/tmp/data.txt_ which provides us with out flag.
```
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{ognOtFam8RM_4An14mgzuRwxq1A.dhTM4QDL3AjN1czW}
```
> FLAG -> pwn.college{ognOtFam8RM_4An14mgzuRwxq1A.dhTM4QDL3AjN1czW}

# GREPPING LIVE OUTPUT
For this chal, we pipe the output of _/challenge/run_ using **|** to _grep pwn.college_. This avoids the need for us to redirect the components of the executable file _/challenge/run_ to another file and then search for it. Piping makes the job much easier. Executing _/challenge/run | grep pwn.college_ provides us with the flag.
```
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{cX8C96Hw8I9f08gzKJzHh90la-r.dlTM4QDL3AjN1czW}
```
> FLAG -> pwn.college{cX8C96Hw8I9f08gzKJzHh90la-r.dlTM4QDL3AjN1czW}

# GREPPING ERRORS
For this chal, as specified in the challenge itself, we redirect the _stderr_ of _/challenge/run_ to _stdout_ using _2>&1_ and then pipe it to grep along with the argument as _pwn.college_ to get our flag.
```
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{0zrAXUaQ0sqaYVjO-uel7VwMexo.dVDM5QDL3AjN1czW}
```
> FLAG -> pwn.college{0zrAXUaQ0sqaYVjO-uel7VwMexo.dVDM5QDL3AjN1czW}

# DUPLICATING PIPED DATA WITH TEE
For this chal, first we try to intercept what is the necessary secret key to pipe the contents of _challenge/pwn_ to _challenge/college_ using _tee_
```
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee whatsthekey | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
```
We proceed to read _whatsthekey_ using cat and get this
```
hacker@piping~duplicating-piped-data-with-tee:~$ cat whatsthekey
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "YJ_hREr8"
```
Voila, we got our secret key! Now we use the key as intented and pass it as a argument to _/challenge/pwn_ and thus get our flag.
```
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret YJ_hREr8 | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{YJ_hREr8lmnDl0vVz0G7tyhDtjh.dFjM5QDL3AjN1czW}
```
> FLAG -> pwn.college{YJ_hREr8lmnDl0vVz0G7tyhDtjh.dFjM5QDL3AjN1czW}

# WRITING TO MULTIPLE PROGRAMS
For this chal, we have duplicate the ouput of _/challenge/hack_ as inputs to _challenge/the_ and _challenge/planet_. So, using _>()_ and _tee_, we can pass the _/challenge/the_ and _/challenge/planet_ files as arguments and the command will write to the following files' _stdin_. Doing so provides us with the flag.
```
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
This secret data must directly and simultaneously make it to /challenge/the and
/challenge/planet. Don't try to copy-paste it; it changes too fast.
21072108501307031145
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{kByLcnoZxJixgbt1zkGwXktivsm.dBDO0UDL3AjN1czW}
hacker@piping~writing-to-multiple-programs:~$
```
> FLAG -> pwn.college{kByLcnoZxJixgbt1zkGwXktivsm.dBDO0UDL3AjN1czW}

# SPLIT-PIPING STDERR AND STDOUT
For this chal, to avoid mixing of _stderr_ and _stdout_, we run _/challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )_ which directs the _stdout_ of _/challenge/hack_ to the _stdin_ of _/challenge/planet_ which read and then redirected as the _stderr_ to the _stdin_ of _/challenge/the_, which provides us with the flag.
```
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >(/challenge/planet) 2> >(/challenge/the)
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{IO_aF_1E9kNvc_e7TL3DS27HD5d.dFDNwYDL3AjN1czW}
```
> FLAG -> pwn.college{IO_aF_1E9kNvc_e7TL3DS27HD5d.dFDNwYDL3AjN1czW}
