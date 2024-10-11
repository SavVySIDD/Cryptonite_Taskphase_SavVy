# Globbing Challenge Report

## 1. Learning About `*` Wildcard

In this level, we learned about the `*` wildcard. When the shell encounters a `*` in any argument, it treats it as a wildcard and replaces the argument with any files that match the pattern.

## 2. Learning About `?` Wildcard

We learned about the `?` wildcard, which matches exactly **one** character. When the shell encounters a `?`, it replaces it with any single character that fits the pattern.

## 3. Learning About `[]` Bracket Globbing

Next, we learned about `[]`, which is a wildcard for a subset of potential characters, specified within the brackets. For example, `[pwn]` will match the characters `p`, `w`, or `n`.

## 4. Using Bracket Globbing to Get the Flag

We used bracket globbing to match specific files while being in the home directory:

## 5. Mixing Commands

I had to use the mix of all commmands learnt in File globbing as here I used `/challenge/run [cep]*`

## 6. Exclusionary Globbing

Here I learnt about `! & ^`, here  the glob inverts, and that bracket instance matches characters that aren't listed. Here I used `/challenge/run [!pwn]*` and got the flag.






