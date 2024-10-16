# LISTING PROCESSES
For this chal, all we have to do is list all the processes using _ps -ef or ps _aux_, which shows us the running renamed _/challenge/run_ program in the process list. We run _/challenge/8354-run-28110_, which provides us with the flag.
```
hacker@processes~listing-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.2  0.0   1056   640 ?        Ss   11:39   0:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bi
root           7  0.0  0.0   5052  2560 ?        S    11:39   0:00 /run/dojo/bin/sleep 6h
root          68  0.0  0.0   4132  2560 ?        S    11:39   0:00 /challenge/8354-run-28110
root          72  0.0  0.0   2744  1600 ?        S    11:39   0:00 sleep 6h
hacker        73  0.3  0.0   5376  3840 pts/0    Ss   11:39   0:00 /run/dojo/bin/ssh-entrypoint
hacker        91  0.0  0.0   7868  3520 pts/0    R+   11:40   0:00 ps aux
hacker@processes~listing-processes:~$ /challenge/8354-run-28110
Yahaha, you found me! Here is your flag:
pwn.college{Iikv9b9kTh6ZJGbEE3Tv7Qcp9eV.dhzM4QDL3AjN1czW}
```
> FLAG -> pwn.college{Iikv9b9kTh6ZJGbEE3Tv7Qcp9eV.dhzM4QDL3AjN1czW}

# KILLING PROCESSES
For this chal, all we had to do was to kill the process _/challenge/dont_run_ by providing is _pid_ as an argument to the _kill_ command. Here the _pid_ is _73_. We run _kill 73_ and after killing the process, we run _/challenge/run_, which provides us with the flag.
```
hacker@processes~killing-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0   1056   640 ?        Ss   12:36   0:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bi
root           7  0.0  0.0   5052  2240 ?        S    12:36   0:00 /run/dojo/bin/sleep 6h
root          71  0.0  0.0   4732  2880 ?        S    12:36   0:00 su -c /challenge/.launcher hacker
hacker        73  0.0  0.0   4976  3520 ?        Ss   12:36   0:00 /challenge/dont_run
hacker        74  0.0  0.0   5052  2560 ?        S    12:36   0:00 sleep 6h
hacker        75  0.0  0.0   5360  3840 pts/0    Ss   12:36   0:00 /run/dojo/bin/ssh-entrypoint
hacker        92  0.0  0.0   7868  3200 pts/0    R+   12:38   0:00 ps aux
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{YGyblCywjA2uJ48TT4DMfV53p4q.dJDN4QDL3AjN1czW}
```
> FLAG -> pwn.college{YGyblCywjA2uJ48TT4DMfV53p4q.dJDN4QDL3AjN1czW}

# INTERRUPTING PROCESSES
For this chal, all we had to do was to was to interrupt the pocees with with _Ctrl-C_ to get the flag.
```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{AEyCTdDgZpTyrGJoQg2L0yOcxQ0.dNDN4QDL3AjN1czW}
```
> FLAG -> pwn.college{AEyCTdDgZpTyrGJoQg2L0yOcxQ0.dNDN4QDL3AjN1czW}

# SUSPENDING PROCESSES
For this chal, we make a copy of _/challenge/run_ and need to suspend the running process using _Ctrl-Z_. After suspending the process, we make another copy of _/challenge/run_ and display it's contents by running _/challenge/run_, which provides us with the flag.
```
hacker@processes~suspending-processes:~$ /challenge/run > copy1
^Z
[1]+  Stopped                 /challenge/run > cock
hacker@processes~suspending-processes:~$ /challenge/run > copy2
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          93      65  0 12:55 pts/0    00:00:00 bash /challenge/run
root         109      65  0 13:02 pts/0    00:00:00 bash /challenge/run
root         111     109  0 13:02 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{Q6h1S7iMWifW0KGgBNDOfQOjSm_.dVDN4QDL3AjN1czW}
```
> FLAG -> pwn.college{Q6h1S7iMWifW0KGgBNDOfQOjSm_.dVDN4QDL3AjN1czW}

# RESUMING PROCESSES
For this chal, first we run _/challenge/run_, then we suspend the running process using _Ctrl-Z_ and then resume the process using the _fg_ command. Doing this provides us with the flag.
```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg /challenge/run
/challenge/run
I'm back! Here's your flag:
pwn.college{8GcMbgS2bG-TsLD9Iaf1TuJ5LJW.dZDN4QDL3AjN1czW}
Don't forget to press Enter to quit me!
```
> FLAG -> pwn.college{8GcMbgS2bG-TsLD9Iaf1TuJ5LJW.dZDN4QDL3AjN1czW}

# BACKGROUNDING PROCESSES
For this chal, first we run _/challenge/run_. then we suspend it using _Ctrl-Z_. Then we resume the process in the background using the _bg_ command. After that we make a copy os _challenge/run_ and then finally run the command to get the flag.
```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S+   bash /challenge/run
root          84 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg /challenge/run
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.
hacker@processes~backgrounding-processes:~$ /challenge/run > copy
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S    bash /challenge/run
root          92 S    sleep 6h
root         105 S+   bash /challenge/run
root         107 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{oRONVHJWCxtXWCMGj-tXYUto5Ho.ddDN4QDL3AjN1czW}
```
> FLAG -> pwn.college{oRONVHJWCxtXWCMGj-tXYUto5Ho.ddDN4QDL3AjN1czW}

# FOREGROUNDING PROCESSES
For this chal, first we run _/challenge/run_, and then suspend it. After that, we run it in the background using _bg_ command and then we bring it to the foreground using the _fg_ command. Doing this provides us with the flag.
```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg /challenge/run
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.
hacker@processes~foregrounding-processes:~$ fg /challenge/run
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{8v0j79Q9lrPaIG14ip8pgKwSJF5.dhDN4QDL3AjN1czW}
```
> FLAG -> pwn.college{8v0j79Q9lrPaIG14ip8pgKwSJF5.dhDN4QDL3AjN1czW}

# STARTING BACKGROUND PROCESSES
For this chal, all we had to do was start _/challenge/run_ as a background process by appending the command with an _&_ character which provides us with the flag.
```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 103



hacker@processes~starting-backgrounded-processes:~$ Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{sOBZ5sthLvjLeVyPEV7qyx9Rc11.dlDN4QDL3AjN1czW}
```
> FLAG -> pwn.college{sOBZ5sthLvjLeVyPEV7qyx9Rc11.dlDN4QDL3AjN1czW}

# PROCESS EXIT CODES
For this chal, we have to get the exit code returned by running _/challenge/get-code_ by providing _echo $?_. It returns _101_. We pass the returned exit code i.e _101_ as an argument to _/challenge/submit-code_, whihc provides us with the flag.
```
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
101
hacker@processes~process-exit-codes:~$ /challenge/submit-code 101
CORRECT! Here is your flag:
pwn.college{kskwBTPLUhoRPUHqXpq9q9jMm4V.dljN4UDL3AjN1czW}
```
> FLAG -> pwn.college{kskwBTPLUhoRPUHqXpq9q9jMm4V.dljN4UDL3AjN1czW}
