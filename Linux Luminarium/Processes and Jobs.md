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
