# Level 18

Log in to the server as `level18` with the password.

    $ ssh -p 2220 bandit18@bandit.labs.overthewire.org
    This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

    bandit18@bandit.labs.overthewire.org's password: kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
    ...
    Byebye !
    Connection to bandit.labs.overthewire.org closed.
    $

It seems like I can't connect.

> The password for the next level is stored in a file readme in the
> homedirectory. Unfortunately, someone has modified .bashrc to log you out
> when you log in with SSH.

I can probably get around this by giving SSH an explicit command to run, in
which case `.bashrc` won't be evaluated.

    $ ssh -p 2220 bandit18@bandit.labs.overthewire.org 'cat readme'
    This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

    bandit18@bandit.labs.overthewire.org's password: kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
    IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
    $

