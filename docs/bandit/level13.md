# Level 13

Login to the server with `bandit13` and the password.

The password for the next level is stored in `/etc/bandit_pass/bandit14` and can
only be read by user `bandit14`. For this level, you don’t get the next password,
but you get a private SSH key that can be used to log into the next level.

    bandit13@bandit:~$ ls
    sshkey.private
    bandit13@bandit:~$ exit

I use `scp` to copy the key to my local machine.

    scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .
    This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

    bandit13@bandit.labs.overthewire.org's password: 
    sshkey.private                                                     100% 1679    76.3KB/s   00:00

I can then use this to log in as `bandit14`, presumably. But only after I change the permissions, since `ssh` complains otherwise.

    $ chmod 600 sshkey.private
    $ ssh -p 2220 bandit14@bandit.labs.overthewire.org -i sshkey.private
    bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
    4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
