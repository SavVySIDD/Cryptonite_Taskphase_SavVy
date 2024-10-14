# Report

## 1st Lesson: Printing Variables with `echo`
In this lesson, I learned how to print variables by using the `echo` command. To print a variable, we prepend it with a `$` symbol. This triggers the variable expansion, allowing the value of the variable to be displayed. For example, using `echo $FLAG` would print the value stored in the `FLAG` variable.

## 2nd Lesson: Assigning Values to Variables
I learned how to assign values to variables. It is important to remember that there should be no spaces when assigning a value to a variable. For example, I used `PWN=COLLEGE`, which successfully assigned the value `COLLEGE` to the `PWN` variable.

## 3rd Lesson: Assigning Values with Spaces
In this lesson, I discovered how to assign values to variables when the values contain spaces. The key is to enclose the value in double quotes. For example, I used `PWN="COLLEGE YEAH"` to assign the value `COLLEGE YEAH` to the `PWN` variable.

## 4th Lesson: The `sh` Command and Exporting Variables
I learned about the `sh` command, which is used to invoke a shell interpreter and start a new shell session. Additionally, I learned that variables are not passed to child processes unless they are exported. I had to store the value `COLLEGE=PWN` and then export `PWN=COLLEGE`. After doing that and running `/challenge/run`, I successfully got the flag.

## 5th Lesson: The `env` Command
In this lesson, I learned about the `env` command, which is used to display the current environment variables or run a command with a modified environment. The command essentially prints all exported variables in the shell, allowing us to see what variables are available.

## 6th Lesson: Storing Command Output in a Variable
Here, I learned how to store the output of a command into a variable. For example, I used `PWN=$(/challenge/run)` to store the result of the `/challenge/run` command into the `PWN` variable. I then printed the variable using `echo $PWN`. I also learned that backticks (`` ` ``) can be used as an alternative to `$()` for command substitution.

## 7th Lesson: Taking User Input with the `read` Command
In this lesson, I learned how to take user input using the `read` command. The `-p` argument is used to provide a prompt message, which separates input from the output. For example, I used `read -p "INPUT:" PWN`, and then provided `COLLEGE` as input, which was stored in the `PWN` variable.
Like here I used 
```
read -p "INPUT:" PWN
INPUT:COLLEGE
```

## 8th Lesson: Redirecting Files with the `read` Command
Finally, I learned how to redirect file content into a variable using the `read` command. By redirecting the input of a file into the command, I was able to store the file's content into a variable. For example, I used `read PWN < /challenge/read_me` and successfully obtained the flag from the file.
```
hacker@dojo:~$ echo "test" > some_file
hacker@dojo:~$ read VAR < some_file
hacker@dojo:~$ echo $VAR
test
```
