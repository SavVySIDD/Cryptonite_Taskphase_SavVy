
# Practicing Piping

## IN 1
We learned about redirecting using `>`. Here I just redirected the output of PWN to COLLEGE using `echo PWN > COLLEGE` and got the flag.

## IN 2
I redirected the output of `/challenge/run` to `myflag` using `/challenge/run > myflag` and then got the flag using the `cat` command.

## IN 3
I learned the difference between `>` and `>>`. The `>` operator truncates and overwrites the data, whereas `>>` appends the data to the existing content. So here I had to append the data as the flag was distributed.

## IN 4
I learned about FD (File Descriptor) numbers, which describe a communication channel in Linux. 
- FD 0: Standard Input
- FD 1: Standard Output
- FD 2: Standard Error

Here it asked to redirect the output and also to redirect the error by using the command `/challenge/run > myflag 2> instructions`, and then using `cat` to get the flag.

## IN 5
I learned about input redirection using `<` Here I has to use `echo COLLEGE > PWN` to make the PWN file contain the value COLLEGE and then redirect input `/challenge/run < PWN` to get the flag.

## IN 6
Here I had to store using FD 1 for getting the output `/challenge/run 1> /tmp/data.txt` and then grepped the value ` grep pwn /tmp/data.txt` and captured the flag.

## IN 7
Here I learnd grepping the live outputs, by using the `|` the pipe operator. Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the command to the right of the pipe. Like here I used ` /challenge/run | grep pwn` to capture the flag.

## IN 8
Here I learnt that since | pipe command redirects only standard output we use '>&' operator to. This means that we can have a two-step process to grep through errors: first, we redirect standard error to standard output (2>& 1) and then pipe the now-combined stderr and stdout as normal (|) . Here I used `/challenge/run 2>&1 | grep "pwn"` to get the flag.

## IN 9
Here this was hard, I had to use piping with Tee which duplicates data flowing through your pipes to any number of files provided on the command line. I used `/challenge/pwn | tee output.txt | /challenge/college` and then by catting the output.txt I got the secret code. And then `/challenge/pwn --secret 8j9QPuJO | /challenge/college` using this I got the flag.

## IN 10
In this challenge, we have /challenge/hack, /challenge/the, and /challenge/planet. Run the /challenge/hack command, and duplicate its output as input to both the /challenge/the and the /challenge/planet commands!
So I used `tee` command in the following way and got the output-
```
acker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the)|tee >(/challenge/planet)
This secret data must directly and simultaneously make it to /challenge/the and 
/challenge/planet. Don't try to copy-paste it; it changes too fast.
407336332703929565
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{gWIbIDSrf0AG_NB4KAZEhb4E68q.dBDO0UDL4YzN0czW}
hacker@piping~writing-to-multiple-programs:~$ 
```

## IN 11
Problem:
Now, let's put your knowledge together. You must master the ultimate piping task: redirect stdout to one program and stderr to another.

The challenge here, of course, is that the | operator links the stdout of the left command with the stdin of the right command. Of course, you've used 2>&1 to redirect stderr into stdout and, thus, pipe stderr over, but this then mixes stderr and stdout. How to keep it unmixed?

You will need to combine your knowledge of ``>(), 2>, and |``. How to do it is a task I'll leave to you.

In this challenge, you have:

/challenge/hack: this produces data on stdout and stderr
/challenge/the: you must redirect hack's stderr to this program
/challenge/planet: you must redirect hack's stdout to this program


```
Connected!
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{UbL_W-AfOcm4_LM9BrACQ9tcpRL.dFDNwYDL4YzN0czW}
hacker@piping~split-piping-stderr-and-stdout:~$
```
