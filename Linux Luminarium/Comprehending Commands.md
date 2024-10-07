# _cat_: NOT THE PET, BUT THE COMMAND!
For this chal, we will use the _cat_ command to display the contents of the _flag_ file present in the _~_ directory, which provides us with the flag.
```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{8JBj-MmYRrA9vPj40WNA5DDGoPp.dFzN1QDL3AjN1czW}
```
> FLAG -> pwn.college{8JBj-MmYRrA9vPj40WNA5DDGoPp.dFzN1QDL3AjN1czW}

# CATTING ABSOLUTE PATHS
For this chal, the _flag_ file is present in the _root(/)_ directory so we use _cat_ on it via providing the absolute path of the file i.e _cat /file_, which displays the content of the file and provides us with the flag.  
An alt way to do this would be to _cd_ to _root_ and simply do _cat flag_, this also provides us with the flag.
```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{kqlEQmzIzQlz5xMN9Fi5zWuXMG7.dlTM5QDL3AjN1czW}

ALT:-
hacker@commands~catting-absolute-paths:~$ cd /
hacker@commands~catting-absolute-paths:/$ cat flag
pwn.college{kqlEQmzIzQlz5xMN9Fi5zWuXMG7.dlTM5QDL3AjN1czW}

```
> FLAG -> pwn.college{kqlEQmzIzQlz5xMN9Fi5zWuXMG7.dlTM5QDL3AjN1czW}

# MORE CATTING PRACTICE
For this chal, the path to the flag file was given by the creator itself when we tried to use _cd_, the path to the flag file is _/usr/include/netrose/flag_. We do _cat /usr/include/netrose/flag_ which displays the content of the file and provides us with the flag.
```
hacker@commands~more-catting-practice:~$ cd
You used 'cd'! In this level, I don't allow you to change the working directory
--- you MUST chase pass 'cat' the absolute path of where I put it on the
filesystem (which is /usr/include/netrose/flag).
hacker@commands~more-catting-practice:~$ cat /usr/include/netrose/flag
pwn.college{gd9p45kMN2wns5L6OEpJwocWWya.dBjM5QDL3AjN1czW}
```
> FLAG -> pwn.college{gd9p45kMN2wns5L6OEpJwocWWya.dBjM5QDL3AjN1czW}

# GREPPING FOR A NEEDLE IN HAYSTACK
For this chal, we use the _grep_ command to search for the flag within the given file _data.txt_. We pass _grep "pwn.college" /challenge/data.txt_ to the shell which provides us with the flag.
```
grep "pwn.college" /challenge/data.txt
pwn.college{4AehqKeX8Lb-3f5oS6oLnb71HhK.ddTM4QDL3AjN1czW}
```
> FLAG -> pwn.college{4AehqKeX8Lb-3f5oS6oLnb71HhK.ddTM4QDL3AjN1czW}

# LISTING FILES
For this chal, we list the contents of challenge directory using _ls /challenge_ to find the executable file of _run_ renamed as _21851-renamed-run-27576_. We execute it and it provides us with the flag.
```
hacker@commands~listing-files:~$ ls /challenge
21851-renamed-run-27576  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/21851-renamed-run-27576
Yahaha, you found me! Here is your flag:
pwn.college{0b8ByXanOROw5gA5qDjMDiNH6-O.dhjM4QDL3AjN1czW}
```
> FLAG-> pwn.college{0b8ByXanOROw5gA5qDjMDiNH6-O.dhjM4QDL3AjN1czW}

# TOUCHING FILES
For this chal, we have to follow the instructions of the chal and create two files named _tmp/pwn_ and _tmp/college_ using _touch_ command. The we execute /challenge/run which provides us with the flag.
```
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{8MBKOjBaReUo72eE-AIqW1s52AJ.dBzM4QDL3AjN1czW}
```
> FLAG -> pwn.college{8MBKOjBaReUo72eE-AIqW1s52AJ.dBzM4QDL3AjN1czW}

# REMOVING FILES
For this chal, we have to remove a file named _delete_me_ from the home directory using the _rm_ command. Then we have to run _/challenge/check_ which checks wheteher the file is deleted or not. If deleted, it returns the flag.
```
hacker@commands~removing-files:~$ touch delete_me
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{cy_gza4DIQTPM2AD-FvLIj0Aigi.dZTOwUDL3AjN1czW}
```
> FLAG -> pwn.college{cy_gza4DIQTPM2AD-FvLIj0Aigi.dZTOwUDL3AjN1czW}

# HIDDEN FILES
For this chal, we have to run _ls / -a_ which lists the hidden files in the _root(/)_ directory. We seem to find this hidden file _.flag-995790357882_. We display its contents using _cat_ which provides us with the flag. 
```
hacker@commands~hidden-files:~$ ls / -a
.   .dockerenv          bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-995790357882  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:~$ cat /.flag-995790357882
pwn.college{oxwIJlXbVerREgjfGRwENsiLfeq.dBTN4QDL3AjN1czW}
```
> FLAG -> pwn.college{oxwIJlXbVerREgjfGRwENsiLfeq.dBTN4QDL3AjN1czW}

# AN EPIC FILESYSTEM QUEST
"I will test you patience with this one" ahh challenge fr. I need not explain a lot about it, using every command and its different usages we learnt till now were used to find files which contained clues after clues to finally get the flag after god knows how many steps. 
```
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
MESSAGE  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin      challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:/$ cat MESSAGE
Tubular find!
The next clue is in: /opt/linux/linux-5.4/drivers/staging/comedi/drivers/ni_routing/ni_route_values

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ cd /opt/linux/linux-5.4/drivers/staging/comedi/drivers/ni_routing/ni_route_values
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/comedi/drivers/ni_routing/ni_route_values$ ls
CLUE  all.h  ni_660x.c  ni_eseries.c  ni_mseries.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/comedi/drivers/ni_routing/ni_route_values$ cat CLUE
Lucky listing!
The next clue is in: /usr/lib/python3/dist-packages/jedi/third_party/typeshed/third_party/2and3/characteristic

hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/comedi/drivers/ni_routing/ni_route_values$ cd /usr/lib/python3/dist-packages/jedi/third_party/typeshed/third_party/2and3/characteristic
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/jedi/third_party/typeshed/third_party/2and3/characteristic$ ls
__init__.pyi
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/jedi/third_party/typeshed/third_party/2and3/characteristic$ ls -a
.  ..  .GIST  __init__.pyi
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/jedi/third_party/typeshed/third_party/2and3/characteristic$ cat .GIST
Lucky listing!
The next clue is in: /usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/STIX/SizeOneSym/Bold

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/jedi/third_party/typeshed/third_party/2and3/characteristic$ cd /usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/STIX/SizeOneSym/Bold
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/STIX/SizeOneSym/Bold$ ls -a
.  ..  .TEASER  All.js  Main.js
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/STIX/SizeOneSym/Bold$ cat .TEASER
Lucky listing!
The next clue is in: /opt/busybox/busybox-1.33.2/include/config/unicode/bidi

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/STIX/SizeOneSym/Bold$ ls /usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/STIX/SizeOneSym/Bold -a
.  ..  .TEASER  All.js  Main.js
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/STIX/SizeOneSym/Bold$ ls /opt/busybox/busybox-1.33.2/include/config/unicode/bidi -a
.  ..  DISPATCH-TRAPPED  support.h
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/STIX/SizeOneSym/Bold$ cat /opt/busybox/busybox-1.33.2/include/config/unicode/bidi/DISPATCH-TRAPPED
Lucky listing!
The next clue is in: /usr/share/perl/5.30.0/Pod/Text
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/STIX/SizeOneSym/Bold$ cat /usr/share/perl/5.30.0/Pod/Text
cat: /usr/share/perl/5.30.0/Pod/Text: Is a directory
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/STIX/SizeOneSym/Bold$ cd /usr/share/perl/5.30.0/Pod/Text
hacker@commands~an-epic-filesystem-quest:/usr/share/perl/5.30.0/Pod/Text$ ls
BLUEPRINT  Color.pm  Overstrike.pm  Termcap.pm
hacker@commands~an-epic-filesystem-quest:/usr/share/perl/5.30.0/Pod/Text$ cat BLUEPRINT
Yahaha, you found me!
The next clue is in: /usr/lib/python3.8/distutils/command

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/share/perl/5.30.0/Pod/Text$ ls /usr/lib/python3.8/distutils/command -a
.              __init__.py  bdist_dumb.py  bdist_wininst.py  build_ext.py      check.py          config.py        install_egg_info.py  install_scripts.py  upload.py
..             __pycache__  bdist_msi.py   build.py          build_py.py       clean.py          install.py       install_headers.py   register.py
TRACE-TRAPPED  bdist.py     bdist_rpm.py   build_clib.py     build_scripts.py  command_template  install_data.py  install_lib.py       sdist.py
hacker@commands~an-epic-filesystem-quest:/usr/share/perl/5.30.0/Pod/Text$ cat /usr/lib/python3.8/distutils/command/TRACE_TRAPPED
cat: /usr/lib/python3.8/distutils/command/TRACE_TRAPPED: No such file or directory
hacker@commands~an-epic-filesystem-quest:/usr/share/perl/5.30.0/Pod/Text$ /usr/lib/python3.8/distutils/command/TRACE_TRAPPED
ssh-entrypoint: /usr/lib/python3.8/distutils/command/TRACE_TRAPPED: No such file or directory
hacker@commands~an-epic-filesystem-quest:/usr/share/perl/5.30.0/Pod/Text$ cat /usr/lib/python3.8/distutils/command/TRACE-TRAPPED
Great sleuthing!
The next clue is in: /opt/angr-management

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/share/perl/5.30.0/Pod/Text$ ls /opt/angr-management -a
.  ..  .POINTER  _internal  angr-management
hacker@commands~an-epic-filesystem-quest:/usr/share/perl/5.30.0/Pod/Text$ cat /opt/angr-management/.POINTER
Lucky listing!
The next clue is in: /opt/linux/linux-5.4/kernel/debug/kdb

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/share/perl/5.30.0/Pod/Text$ cd /opt/linux/linux-5.4/kernel/debug/kdb
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/kernel/debug/kdb$ ls
Makefile  TIP  kdb_bp.c  kdb_bt.c  kdb_cmds  kdb_debugger.c  kdb_io.c  kdb_keyboard.c  kdb_main.c  kdb_private.h  kdb_support.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/kernel/debug/kdb$ cat TIP
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{QEOURkKbn9J9KP7ka1QRgGbj1d8.dljM4QDL3AjN1czW}
```
>FLAG -> pwn.college{QEOURkKbn9J9KP7ka1QRgGbj1d8.dljM4QDL3AjN1czW}

# MAKING DIRECTORIES
For this chal, we had to make a new directory _/tmp/pwn_ using the _mkdir_ command. The we had to create a file named _college_ in it using the _touch_ command. Then we ran our favourite _challenge/run_ to get the flag.
```
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ cd /tmp/pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{EMkM5QB_HiXfvocDHuxaxeC2yRV.dFzM4QDL3AjN1czW}
```
> FLAG -> pwn.college{EMkM5QB_HiXfvocDHuxaxeC2yRV.dFzM4QDL3AjN1czW}

# FINDING FILES
For this chal, we had to _cd_ to _root(/)_ and then apply _find -name "flag"_ which would list all the files and directories which contain any file named _flag_. It listed many files and directories and I tried to access only those which did not come with the error message _"Permission Denied"_. I found the flag in _./usr/share/doc/libavahi-client3/_ directory.
```
hacker@commands~finding-files:/$ find -name "flag"
find: ‘./tmp/tmp.MiOQGWw5Zc’: Permission denied
find: ‘./etc/ssl/private’: Permission denied
./usr/local/lib/python3.8/dist-packages/pwnlib/flag
./usr/local/share/radare2/5.9.5/flag
./usr/share/doc/libavahi-client3/flag
find: ‘./var/cache/apt/archives/partial’: Permission denied
find: ‘./var/cache/ldconfig’: Permission denied
find: ‘./var/cache/private’: Permission denied
find: ‘./var/lib/apt/lists/partial’: Permission denied
find: ‘./var/lib/mysql-files’: Permission denied
find: ‘./var/lib/private’: Permission denied
find: ‘./var/lib/mysql’: Permission denied
find: ‘./var/lib/mysql-keyring’: Permission denied
find: ‘./var/lib/php/sessions’: Permission denied
find: ‘./var/log/private’: Permission denied
find: ‘./var/log/apache2’: Permission denied
find: ‘./var/log/mysql’: Permission denied
find: ‘./run/mysqld’: Permission denied
find: ‘./run/sudo’: Permission denied
find: ‘./root’: Permission denied
./opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
./opt/radare2/libr/flag
find: ‘./proc/tty/driver’: Permission denied
find: ‘./proc/1/task/1/fd’: Permission denied
find: ‘./proc/1/task/1/fdinfo’: Permission denied
find: ‘./proc/1/task/1/ns’: Permission denied
find: ‘./proc/1/fd’: Permission denied
find: ‘./proc/1/map_files’: Permission denied
find: ‘./proc/1/fdinfo’: Permission denied
find: ‘./proc/1/ns’: Permission denied
find: ‘./proc/7/task/7/fd’: Permission denied
find: ‘./proc/7/task/7/fdinfo’: Permission denied
find: ‘./proc/7/task/7/ns’: Permission denied
find: ‘./proc/7/fd’: Permission denied
find: ‘./proc/7/map_files’: Permission denied
find: ‘./proc/7/fdinfo’: Permission denied
find: ‘./proc/7/ns’: Permission denied
FOUND FLAG AT :-
hacker@commands~finding-files:/$ cd ./usr/share/doc/libavahi-client3/
hacker@commands~finding-files:/usr/share/doc/libavahi-client3$ ls
NEWS.gz  README  changelog.Debian.gz  copyright  flag
hacker@commands~finding-files:/usr/share/doc/libavahi-client3$ cat flag
pwn.college{Y8CX9jOkOSQ20Cm-XHeA5EXptcy.dJzM4QDL3AjN1czW}
```
> FLAG ->pwn.college{Y8CX9jOkOSQ20Cm-XHeA5EXptcy.dJzM4QDL3AjN1czW}

# LINKING FILES
In this chal, we had to create a symlink between two files, the given file _/flag_ and another _not-the-flag_ in the home directory. _not-the-flag_ file acts as a pointer to _/flag_. We use _/challenge/catflag_ to print the contents of _/flag_ via the symlink file _not-the-flag_ and thus, get the flag.
```
hacker@commands~linking-files:~$ ln -s /flag ~/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{QhQpIzrd1Pshi7Zs7kOCx0NDAvO.dlTM1UDL3AjN1czW}
```
> FLAG -> pwn.college{QhQpIzrd1Pshi7Zs7kOCx0NDAvO.dlTM1UDL3AjN1czW}
