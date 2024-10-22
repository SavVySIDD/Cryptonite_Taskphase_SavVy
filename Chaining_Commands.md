# Chaining Commands
## IN 1
The easiest way to chain commands is ;. In most contexts, ; separates commands in a similar way to how Enter separates lines.
Here I just chained just two commands and got the flag-
```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn ; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{Q6Xvqn2jSsQYD6H6f0sf_hieOSK.dVTN4QDL4YzN0czW}
hacker@chaining~chaining-with-semicolons:~$ 
```

## IN 2
As you combine more and more commands to achieve complex effects, the length of the combined prompt quickly gets really annoying to deal with. 
When this happens, you can put these commands in a file, called a shell script, and run them by executing the file!
I got the file using 
```
hacker@chaining~your-first-shell-script:~$ nano x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{g2g5sa1BZuGm8vyQ8-3HZOThaib.dFzN4QDL4YzN0czW}
hacker@chaining~your-first-shell-script:~$ 
```
After writing nano.sh I had to add the following commands in it-"/challenge/pwn /challenge/college".
`nano` is a simple, terminal-based text editor commonly used in Linux and macOS. It allows you to create, edit, and save text files directly in the terminal.

## IN 3
As far as the shell is concerned, your script is just another command. That means you can redirect its input and output just like you did for commands in the Piping module!
Here I got the flag using - 
```
hacker@chaining~redirecting-script-output:~$ nano p.sh
hacker@chaining~redirecting-script-output:~$ cat p,sh
cat: p,sh: No such file or directory
hacker@chaining~redirecting-script-output:~$ cat p.sh
/challenge/pwn
/challenge/college
hacker@chaining~redirecting-script-output:~$ bash p.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{8SkFH3oavZnq4bo3z69_nQR2g8A.dhTM5QDL4YzN0czW}
hacker@chaining~redirecting-script-output:~$ 
```

## IN 4
Here I learned it is not required to use `bash` always to run the file. 
If your shell script file is executable (recall File Permissions), you can simply invoke it via its relative or absolute path! For example, if you create script.sh in your home directory and make it executable, you can invoke it via `/home/hacker/script.sh` or `~/script.sh `or (if your working directory is /home/hacker) `./script.sh`.
Here I got the flag using-
```
hacker@chaining~executable-shell-scripts:~$ nano pr.sh
hacker@chaining~executable-shell-scripts:~$ ls
COLLEGE  PWN  college  instructions  not-the-flag  p.sh   pwn       var
Desktop  a    grep     myflag        output.txt    pr.sh  the-flag  x.sh
hacker@chaining~executable-shell-scripts:~$ ./pr.sh
ssh-entrypoint: ./pr.sh: Permission denied
hacker@chaining~executable-shell-scripts:~$ /home/hacker/script.sh
ssh-entrypoint: /home/hacker/script.sh: No such file or directory
hacker@chaining~executable-shell-scripts:~$ pws
ssh-entrypoint: pws: command not found
hacker@chaining~executable-shell-scripts:~$ pwd
/home/hacker
hacker@chaining~executable-shell-scripts:~$ /home/hacker/pr.sh
ssh-entrypoint: /home/hacker/pr.sh: Permission denied
hacker@chaining~executable-shell-scripts:~$ chmod +x pr.sh
hacker@chaining~executable-shell-scripts:~$ /home/hacker/pr.sh
Congratulations on your shell script execution! Your flag:
pwn.college{MMelZQMRp0GqSszncaVgzvYSwhI.dRzNyUDL4YzN0czW}
hacker@chaining~executable-shell-scripts:~$
```

