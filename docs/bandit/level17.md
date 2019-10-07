# Level 17

Log in to the server with `bandit17` and the key.

> There are 2 files in the homedirectory: *passwords.old* and *passwords.new*.
> The password for the next level is in *passwords.new* and is the only line
> that has been changed between passwords.old and *passwords.new*.

This is easy. I can just use the `diff` utility to give me a list of
differences between the two files.

    bandit17@bandit:~$ diff passwords.{old,new}
    42c42
    < hlbSBPAWJmL6WFDb06gpTx1pPButblOA
    ---
    > kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
    bandit17@bandit:~$ 

The key in the last line is the password.
