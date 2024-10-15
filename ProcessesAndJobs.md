# Command Line Challenges Report

## 1. `ps` Command - Process Status
The `ps` command stands for "process status". It lists processes running in the terminal.

### Syntax Variations
- **Standard Syntax**: You can use `-e` to list "every" process and `-f` for a "full format" output. These can be combined into a single argument `-ef`.
- **BSD Syntax**: You can use `a` to list processes for all users, `x` to list processes that aren't running in a terminal, and `u` for a "user-readable" output. These can be combined into a single argument `aux`.

### Common Outputs
Both syntax variations typically display the following columns:
- **USER**: The user running the process
- **PID**: The Process ID
- **TTY**: The terminal associated with the process
- **STIME/START**: The start time of the process
- **TIME**: The total CPU time used by the process
- **CMD/COMMAND**: The command used to start the process

I identified the required file by searching for a similar process running in the terminal and retrieved the flag.

## 2. Killing Processes Using `kill`
The `kill` command is used to terminate processes using their Process IDs (PIDs). I had to kill the process `/challenge/dont_run` by using its PID, which gave me the flag.

## 3. Interrupting a Process - `Ctrl+C`
I learned how to interrupt a running process using `Ctrl+C`.

## 4. Suspending a Process - `Ctrl+Z`
I learned how to suspend a running process using `Ctrl+Z`.

## 5. Resuming a Suspended Process - `fg`
The `fg` command brings a suspended process back to the foreground.

## 6. Backgrounding Processes with `bg`
We can also resume suspended processes in the background using the `bg` command.

### Example:

- The `T` in `sleep`'s status indicates that it is suspended.
- `S` in bash’s status shows it’s sleeping, waiting for input.
- `R+` in `ps`'s status means it's running in the foreground.

After resuming the `sleep` process in the background:

Now the `sleep` process is running in the background (status `S`), and it no longer has the `+` since it's not in the foreground.

## 7. Foregrounding a Background Process
Using `fg` again after `bg`, I learned that you can bring a background process back to the foreground.

## 8. Starting a Process in the Background
You can start a process directly in the background by appending an `&` to the command.

## 9. Exit Codes
Every shell command exits with an exit code. You can access the exit code of the most recently-terminated command using the special variable `$?`. 

- Successful commands typically return `0`.
- Failed commands return a non-zero value, often `1` but sometimes a more specific error code.

Example:
