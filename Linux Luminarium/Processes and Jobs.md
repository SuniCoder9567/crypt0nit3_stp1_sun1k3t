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

