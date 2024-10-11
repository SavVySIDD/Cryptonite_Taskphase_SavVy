
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
