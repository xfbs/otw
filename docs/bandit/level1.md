# Level 1

Use the password to log in to the server with user `bandit1`.

    $ ssh -p 2220 bandit1@bandit.labs.overthewire.org
    This is a OverTheWire game server. More information on http://www.overthewire.org/wargame

    bandit1@bandit.labs.overthewire.org's password: boJ9jbbUNNfktd78OOpsqOltutMc3MY1

    bandit1@bandit:~$ 

The password for the next level is stored in a file named `-` located in the home directory.

    bandit1@bandit:~$ ls
    -
    bandit1@bandit:~$ echo $(< -)
    CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9

