# Pondering PATH
First of all path and PATH are not the same thing, there's a lot of difference between them-

### -path: 
Refers to the location of a specific file or directory in the filesystem, such as `/home/user/documents/file.txt`.
### -PATH: 
Refers to an environment variable that stores a list of directories where the system looks for executable programs. When you run a command, the system searches the directories in `PATH` to find the corresponding executable file.
It is useful as -
concentrating by default of most executable files in just a few directories rather than spread all over the filesystem and the use of the PATH variable to find them eliminates the need for users to remember which directories they are in and to type their absolute path names. 
That is, any such program can be run by merely typing its name, such as ls instead of /bin/ls and head instead of /usr/bin/head, regardless of where the user is currently working on the filesystem.

A list of all the current environmental variables and their values for the current user, including all the directories in the PATH variable, can be seen by running the `env `command without any options or arguments.
To just display the PATH environmental variable and its value- 
we can use `env | grep PATH` or also we can use `echo $PATH`.

Thus far, you have invoked commands in several ways:

- Through an absolute path (e.g., /challenge/run).
- Through a relative path (e.g., ./run).
- Through a bare command name (e.g., ls).
The first two cases, the absolute and the relative path case, are straightforward: the run file lives in the /challenge directory, and both cases refer to it
There is a special shell variable, called `PATH`, that stores a bunch of directory paths in which the shell will search for programs corresponding to commands, including PATH.

## IN 1st
I learned If you blank out the variable, things go badly:
```
hacker@dojo:~$ ls
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$ PATH=""
hacker@dojo:~$ ls
bash: ls: No such file or directory
hacker@dojo:~$
```
Without a PATH, bash cannot find the ls command


I just had to change the PATH variable so that it cannot find the rm command -
```
hacker@path~the-path-variable:~$ env | grep PATH
PATH=/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~the-path-variable:~$ echo $PATH
/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{gBmp6dBSyGO5KxJBCpYUcP_jYgK.dZzNwUDL4YzN0czW}
hacker@path~the-path-variable:~$ 
```
## IN 2
I learned how to add a new directory of programs to our command repertoire.
If you maintain useful scripts that you want to be able to launch by bare name u you need to add it to the path variable
```
hacker@dojo:~$ ls /home/hacker/scripts
goodscript	badscript	okayscript
hacker@dojo:~$ goodscript
bash: goodscript: command not found
hacker@dojo:~$ /home/hacker/scripts/goodscript
YEAH! This is the best script!
hacker@dojo:~l
```
Here I wanted to run goodsript directly, for that I had to add it to the `PATH ` variable.
```
hacker@dojo:~$ PATH=/home/hacker/scripts
hacker@dojo:~$ goodscript
YEAH! This is the best script!
hacker@dojo:~$
```
A similar situation was given in the problem statement so I captured the flag using- 
```
hacker@path~setting-path:~$ ls /challenge/more_commands
win
hacker@path~setting-path:~$ PATH = /challenge/more_commands/
ssh-entrypoint: PATH: command not found
hacker@path~setting-path:~$ PATH=/challenge/more_commands/
hacker@path~setting-path:~$ win
It looks like 'win' was improperly launched. Don't launch it directly; it MUST 
be launched by /challenge/run!
hacker@path~setting-path:~$ /challenge/run win
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{o_Q3O2Sqw7_v3mt-lthfuPdFLNE.dVzNyUDL4YzN0czW}
hacker@path~setting-path:~$ 
```

## IN 3
I learned about renaming a file using `mv` command.
Here I combined the knowledge of creating a file while adding details to it. And then adding its Path to the `PATH` and then capturing the flag using `/challenge/run`
Here I first created a file named win using `nano win` and then added `cat /flag` to it. And then added its path to the existing PATH using `PATH=/home/hacker/:$PATH
` or we can also use `PATH=$PATH:/home/hacker` it just changes the position nothing else.
```
COLLEGE  a        instructions  not-the-flag  pr.sh     var
Desktop  college  lost+found    output.txt    pwn       win.sh
PWN      grep     myflag        p.sh          the-flag  x.sh
hacker@path~adding-commands:~$ echo $PATH
/home/hacker:/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/home/hacker
hacker@path~adding-commands:~$ mv win.sh win
hacker@path~adding-commands:~$ ls
COLLEGE  a        instructions  not-the-flag  pr.sh     var
Desktop  college  lost+found    output.txt    pwn       win
PWN      grep     myflag        p.sh          the-flag  x.sh
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{EHiHdvcrVJMgLbSXlkVDgi0W3oN.dZzNyUDL4YzN0czW}
hacker@path~adding-commands:~$ 
```

## IN 4
I had to attach the path of `/home/hacker` at first in the `PATH` variable using `PATH=/home/hacker:$PATH`
Then I manually created a rm using `nano rm` and added the content `#!/bin/bash
/bin/cat /flag` in the rm.
And then ran `/challenge/run` to get the flag and as it was automatically running rm it found it first at /home/hacker and gave the flag.
