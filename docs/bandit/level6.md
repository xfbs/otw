# Level 6

Connect to the server using `bandit6` as username and the password.

> The password for the next level is stored somewhere on the server and has all
> of the following properties: owned by user `bandit7`, owned by group `bandit6`,
> 33 bytes in size

This time I use the `find` command to search the whole filesystem for a file
matching the specifications.

    bandit6@bandit:~$ find / -size 33c -user bandit7 -group bandit6 2> /dev/null
    /var/lib/dpkg/info/bandit7.password
    bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
    HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
