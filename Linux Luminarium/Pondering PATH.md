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

