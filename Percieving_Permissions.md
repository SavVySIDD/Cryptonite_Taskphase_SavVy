# File Permissions and Ownership Challenges
## IN this module I learnt about `ls-l` command which can check out a permissions of a file or directory. I learnd about chmod calculator 'https://chmod-calculator.com/'.
The first character of each line represents the file type. (d, represents directory and -,represents normal file).
The next nine characters are the actual access permissions of the file or directory, split into 3 characters 1st 3 for Owner next 3 for Group and last 3 for Public.
r-read, w-wrie, x-execute


## IN 1st 
we can change the ownership of files! This is done via the `chown (change owner)` command, but chown can only be invoked by the root user. Here i just used `chown hacker /flag` to give the access to the hacker directory from root directory and got the flag by catting /flag.

## IN 2nd 
we can check which group are we a part of by `id` command, Files have both an owning user and group. Group ownership can be changed with the `chgrp` (change group) command. Here in this challenge I got the flag using `chgrp hacker /flag` and then got the flag by catting it.
Basically I changed the ownership of the group from root to hacker.

## IN 3rd 
I had to find the group name using `id` command as:
```
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp32383) groups=1000(grp32383)
```
and then got the flag using 
```
hacker@permissions~fun-with-groups-names:~$ chgrp grp32383 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{kzV09HtNq-G7xxSmDa3dF4FB9_a.dJzNyUDL4YzN0czW}
```

## IN 4th 
we learn
```
r - user/group/other can read the file (or list the directory)
w - user/group/other can modify the files (or create/delete files in the directory)
x - user/group/other can execute the file as a program (or can enter the directory, e.g., using `cd`)
- - nothing 
```
Like ownership, file permissions can also be changed using `chmod`.
`chmod [OPTIONS] MODE FILE`

You can specify the MODE in two ways: as a modification of the existing permissions mode, or as a completely new mode to overwrite the old one.
chmod allows you to tweak permissions with the mode format of `WHO+/-WHAT`
ex:
u+r, as above, adds read access to the user's permissions
g+wx adds write and execute access to the group's permissions
o-w removes write access for other users
a-rwx removes all permissions for the user, group, and world

Here basically used chmod `+r` to change permission of group and other of /flag file to -r for everyone(u,g&o).

## IN 5th 
basically I had to make the file executable using `+x`. I used `chmod a+x /challenge/run` and then got the flag using `challenge/run`

## IN 6th 
I had to perform multiple steps to modify the ownership and file permissions using `chmod` and finally got the flag after completing 8 rounds.

## IN 7th j
ust learned a different method of using chmod as `chmod u=rw,g=r,o=- /challenge/pwn` for changing permissions and everything similar to 6th.

## IN 8th 
I leared about SUID. The "Set User ID" (SUID) permissions bit allows the user to run a program as the owner of that program's file.
The "Set User ID" (SUID) bit is a special file permission in Linux that allows a program to be executed with the privileges of the file's owner, rather than the user running the program. This is particularly useful when regular (non-root) users need to perform tasks that require elevated privileges without giving them full root access or requiring the administrator to be involved each time.(ChatGPT)

```
hacker@dojo:~$ ls -l /usr/bin/sudo
-rwsr-xr-x 1 root root 232416 Dec 1 11:45 /usr/bin/sudo
hacker@dojo:~$
```
The s part in place of the executable bit means that the program is executable with SUID. It means that, regardless of what user runs the program (as long as they have executable permissions), the program will execute as the owner user (in this case, the root user).

Here just used `chmod u+s /challenge/getroot` to add the SUID bit, in order to spawn a root shell to cat the flag ourself.
and then ran `/challenge/getroot` and then got the flag by `cat/flag`.





