# Digesting_Documentation


## Step 1: Finding the Flag

Used the `find` command to locate the flag file, suppressing errors with `2>/dev/null`:

`find /challenge/challenge -name flag 2>/dev/null`

## Step 2: Retrieving the Flag

After locating the flag, used the challenge program to print the flag content:

`/challenge/challenge --printfile ./flag`

## Step 3: Consulting the Manual

Opened the manual for the `challenge` program to explore available options:

`man challenge`

Found the argument to retrieve the flag:

`/challenge/challenge --wtnthn 683`

## Step 4: Searching in Manual

Used the manual search functionality to find occurrences of the keyword "flag":

`/flag`

Navigated through results using `n` to find relevant information.

## Step 5: Understanding the `man` Command

Reviewed the manual for the `man` command to learn more about navigating manuals efficiently:

`man man`

## Step 6: Using Help Option

Utilized the `--help` option to discover more about the challenge and the secret key:

`/challenge/challenge --help`

Finally, used the secret key to retrieve the flag:

`/challenge/challenge --wtnthn 683`

## Step 7: Using Shell Built-ins

Learned about shell built-ins by using the `help` command:

`help`

This provided additional insights into the available commands.
