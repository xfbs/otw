# Level 11

Login to the server with `bandit11` and the password.

The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

I can use the `tr` utility to translate sets of characters. So essentially I need to come up with a way to generate the character lists.

Using some bash primitives and `tr`, I can construct character lists for the alphabet.

    bandit11@bandit:~$ echo {a..z} | tr -d "[:space:]"
    abcdefghijklmnopqrstuvwxyz
    bandit11@bandit:~$ echo {n..z} {a..n} | tr -d "[:space:]"
    nopqrstuvwxyzabcdefghijklmn

I can use this part to translate one half (lower-case characters) already.

    bandit11@bandit:~$ cat data.txt | tr `echo {a..z} | tr -d "[:space:]"` `echo {n..z} {a..n} | tr -d "[:space:]"`
    Ghe password is 5Ge8L4drgPEfPx8ugdwuRK8XSP6k2RHu

And I apply the same thing but with uppercase characters to get it fully rotated.

    bandit11@bandit:~$ cat data.txt | tr `echo {a..z} | tr -d "[:space:]"` `echo {n..z} {a..n} | tr -d "[:space:]"` | tr `echo {A..Z} | tr -d "[:space:]"` `echo {N..Z} {A..N} | tr -d "[:space:]"`
    The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu

I am sure there is a simpler or more optimal way, but at least this is original.
