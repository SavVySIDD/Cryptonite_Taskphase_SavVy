IN 1st about `ps` command stands for "process status". It just lists process running in the terminal.
We need to pass a few arguments:
"Standard" Syntax: in this syntax, you can use -e to list "every" process and -f for a "full format" output, including arguments. These can be combined into a single argument -ef.
"BSD" Syntax: in this syntax, you can use a to list processes for all users, x to list processes that aren't running in a terminal, and u for a "user-readable" output. These can be combined into a single argument aux.
Commonly both display the user (USER column), the PID, the TTY, the start time of the process (STIME/START), the total utilized CPU time (TIME), and the command (CMD/COMMAND)
Here the file name was changed, but was running in the terminal so i just found the similar file and got the flag.


IN 2nd I learnt about killing processes using `kill` command combined with PID's (Process IDs), Here I just had to kill the /challenge/dont_run using its PID and got the flag 

IN 3rd I learnt about Interrupting process using `ctrl+c`

IN 4th I learnt about Suspnding Process using `ctrl+z`

IN 5th I learnt about Resuming Process using `fg` 
