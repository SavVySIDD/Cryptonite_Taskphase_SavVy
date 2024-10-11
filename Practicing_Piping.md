
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
