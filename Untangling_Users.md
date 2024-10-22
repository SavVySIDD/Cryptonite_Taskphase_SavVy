# Untangling Users
# IN 1
Becoming root is a fairly common action that Linux users take, there are two utilities used for this purposes: `su `and `sudo`.
su is a setuid binary, Because it has the SUID bit set, su runs as root. Running as root, it can start a root shell! Of course, 
su is discerning: before allowing the user to elevate privileges to root, it checks to make sure that the user knows the root password,
So basically, here the flag was given I just had to use `su` and type the provided password to get the flag.

# IN 2
With no arguments, su will start a root shell (after authenticating with root's password). However, you can also give a username as an argument to switch to that user instead of root.
Here I just had to use `su zardus` and then type the provided password and then run `/challenge/run` to get the flag.

# IN 3
When you enter a password for su, it compares it against the stored password for that user. These passwords used to be stored in /etc/passwd, 
but because /etc/passwd is a globally-readable file, this is not good for passwords, these were moved to /etc/shadow.
Separated by :s, the first field of each line is the username and the second is the password. 
A value of `*` or `!` functionally means that password login for the account is disabled, a blank field means that there is no password 
When you input a password into su, it one-way-encrypts (hashes) it and compares the result against the stored value. If the result matches, su grants you access to the user!
Even though you don't know the password, If you have the hashed value of the password, you can crack it!
If a hacker gets their hands on a leaked `/etc/shadow`, they can start cracking passwords and wreaking havoc. The cracking can be done via the famous John the Ripper, as so
```
hacker@dojo:~$ john ./my-leaked-shadow-file
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Will run 32 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
password1337      (zardus)
1g 0:00:00:22 3/3 0.04528g/s 10509p/s 10509c/s 10509C/s lykys..lank
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@dojo:~$
```
Here, John the Ripper cracked Zardus' leaked password hash to find the real value of password1337.
Similarly, I got the flag using, 
```
Last login: Wed Oct 23 00:50:40 on ttys000
siddhanbaranwal@Siddhans-Laptop ~ % ssh -i key hacker@pwn.college
                                                                                Connected!
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:03 35% 1/3 0g/s 206.4p/s 206.4c/s 206.4C/s zzardus99999..Ozardus
0g 0:00:00:15 0% 2/3 0g/s 195.5p/s 195.5c/s 195.5C/s 123456
0g 0:00:00:18 0% 2/3 0g/s 213.5p/s 213.5c/s 213.5C/s serena..88888888
0g 0:00:00:20 0% 2/3 0g/s 220.9p/s 220.9c/s 220.9C/s national..rocket1
0g 0:00:00:21 1% 2/3 0g/s 223.6p/s 223.6c/s 223.6C/s 1234qwer..babygirl
0g 0:00:00:22 1% 2/3 0g/s 225.1p/s 225.1c/s 225.1C/s katrina..karla
aardvark         (zardus)
1g 0:00:00:25 100% 2/3 0.03937g/s 229.2p/s 229.2c/s 229.2C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password: 
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{EIW6QkteN9I0RdTgvrie_gySfwi.ddTN0UDL4YzN0czW}
zardus@users~cracking-passwords:/home/hacker$ 
```

# IN 4
Since root passwords are vulnerable to attacks, and can leak.
To address this, in recent decades, the world has moved from administration via su to administration via sudo
Unlike su, which defaults to launching a shell as a specified user, sudo defaults to running a command as root:
```
hacker@dojo:~$ whoami
hacker
hacker@dojo:~$ sudo whoami
root
hacker@dojo:~$
```
Here we basically get the sudo acess, so I got the flag using `sudo cat /flag`.
