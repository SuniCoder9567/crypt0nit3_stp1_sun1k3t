# THE PATH VARIABLE
For this chal, all we have to do is mess with eh `PATH Variable`, which contains a bunch of directory paths, including `rm`. If we reset the `PATH` variable, the shell will not be able to access the rm command, and we will get our flag.
```
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{Yggjmzpt9drWADR0RUARtBJ1tk1.dZzNwUDL3AjN1czW}
```
> FLAG -> pwn.college{Yggjmzpt9drWADR0RUARtBJ1tk1.dZzNwUDL3AjN1czW}

# SETTING PATH
For this chal, we need to type in the directory path of the `win` command to the `PATH` variable. The path to `win` is `/challenge/more_commands`. After doing so, we need to execute `/challenge/run`, which provides us with the flag.
```
hacker@path~setting-path:~$ PATH="/challenge/more_commands"
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{sscy_0xDu-OvXz7boyGMI9LYv-7.dVzNyUDL3AjN1czW}
```
> FLAG -> pwn.college{sscy_0xDu-OvXz7boyGMI9LYv-7.dVzNyUDL3AjN1czW}

# ADDING COMMANDS
For this chal, we need to first create and executable script named `win` in which we need to add the command `cat /flag`. Then we have to make it executable using `chmod +x`. After that, we need to add the path of the `win` script, in this case `~`, to the existing path variables seperated by `:`. Then we execute `/challenge/run`, whcih provides us with the flag.
```
hacker@path~adding-commands:~$ nano win
hacker@path~adding-commands:~$ echo $PATH
/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~adding-commands:~$ PATH="/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:~"
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{4uw_y8cSQfjiJ_XqU5B6qD1KLTV.dZzNyUDL3AjN1czW}
```
> FLAG -> pwn.college{4uw_y8cSQfjiJ_XqU5B6qD1KLTV.dZzNyUDL3AjN1czW}

# HIJACKING COMMANDS
I LOVED THIS CHAL SO MUCH! For this one, first I was just wondering how do I go about this when I can't get the flag out of `/challenge/run`. SO i used `nano` to look into into it and all I saw was a simple call to the `rm` command along with the attribute `flag`. Then it hit me, how about I literally change how `rm` works. I created a new executable file `rm` in my `home` directory and gave the command `/usr/bin/cat /flag` (reason being, once I change the path I wont get to use cat directly). THen I changed my `PATH` variable's value to `~`. After that, running /challenge/run provided me with the flag.
```
hacker@path~hijacking-commands:~$ nano rm
hacker@path~hijacking-commands:~$ chmod a+x rm
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
pwn.college{sR7_e0RztOUFOzWxBjqQbrXD8d_.ddzNyUDL3AjN1czW}
```
> FLAG -> pwn.college{sR7_e0RztOUFOzWxBjqQbrXD8d_.ddzNyUDL3AjN1czW}


