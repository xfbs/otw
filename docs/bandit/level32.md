# Level 32

Log into the server as `bandit32` and the password.

> After all this git stuff its time for another escape. Good luck!

I am greeted by

    WELCOME TO THE UPPERCASE SHELL
    >> ls
    sh: 1: LS: not found
    >>

It seems to be some kind of shell that transforms everything it receives to uppercase characters before it executes it. It would be easier if this was on a macOS machine, because with their case-insensitive default filesystem, this wouldn't be an issue. 

I play around with the shell, and consult the manpage a bit, trying to find any kind of hint. Ideally, I want to be able to execute a normal shell.

By luck, I manage to figure it out. I use the variable `$0`, which seems to be set to `/bin/sh`.

    >> $0
    $ ls
    uppershell
    $ pwd
    /home/bandit32
    $

From this shell, I am able to retrieve the password for the next level.

    $ cat /etc/bandit_pass/bandit33
    c9c3199ddf4121b10cf581a98d51caee

