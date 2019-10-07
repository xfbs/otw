# Level 26

Log in to the server with `level26` and the password. Make sure the terminal
window is set small enough so that `more` will run.

With `more` active, press `v` to launch Vim. Vim has a built-in shell feature
that can be run by typing in `:shell`, but this doesn't work yet because it
is still using the phony shell that the user has set. So I used

    :set shell=/bin/bash
    :shell

To launch a proper and useful shell.

    bandit26@bandit:~$ ls
    bandit27-do  text.txt

There is a setuid executable, `bandit27-do`, that I used to get the password.

    bandit26@bandit:~$ ./bandit27-do cat /etc/bandit_pass/bandit27
    3ba3118a22e93127a4ed485be72ef5ea
    bandit26@bandit:~$ 

