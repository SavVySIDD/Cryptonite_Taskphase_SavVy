IN this module I learnt about `ls-l` command which can check out a permissions of a file or directory. I learnd about chmod calculator 'https://chmod-calculator.com/'.
The first character of each line represents the file type. (d, represents directory and -,represents normal file).
The next nine characters are the actual access permissions of the file or directory, split into 3 characters 1st 3 for Owner next 3 for Group and last 3 for Public.
r-read, w-wrie, x-execute


IN 1st we can change the ownership of files! This is done via the `chown (change owner)` command, but chown can only be invoked by the root user. Here i just used `chown hacker /flag` to give the access to the hacker directory from root directory and got the flag by catting /flag.

IN 2nd 
