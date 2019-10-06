# Level 0

Connect to `bandit.labs.overthewire.org` on port 2220. The username is `bandit0` and the password is `bandit0`.

    $ ssh bandit0@bandit.labs.overthewire.org -p 2220
    The authenticity of host '[bandit.labs.overthewire.org]:2220 ([176.9.9.172]:2220)' can't be established.
    ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
    Are you sure you want to continue connecting (yes/no)? yes
    This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

    bandit0@bandit.labs.overthewire.org's password: bandit0
    bandit0@bandit$ 

Locate a file called `readme` in the home directory and get the password for level 1 from it.

    bandit0@bandit$ ls
    readme
    bandit0@bandit$ cat readme
    boJ9jbbUNNfktd78OOpsqOltutMc3MY1


