# Level 5

Connect to server with username `bandit5` and the password.

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

* human-readable
* 1033 bytes in size
* not executable

    bandit5@bandit:~$ ls inhere
    maybehere00  maybehere03  maybehere06  maybehere09  maybehere12  maybehere15  maybehere18
    maybehere01  maybehere04  maybehere07  maybehere10  maybehere13  maybehere16  maybehere19
    maybehere02  maybehere05  maybehere08  maybehere11  maybehere14  maybehere17
    bandit5@bandit:~$ ls inhere/*
    inhere/maybehere01:
    -file1  -file2  -file3  spaces file1  spaces file2  spaces file3

    inhere/maybehere02:
    -file1  -file2  -file3  spaces file1  spaces file2  spaces file3

    ...
    bandit5@bandit:~$ ls -la inhere/* | grep -B 6 1033
    inhere/maybehere07:
    total 56
    drwxr-x---  2 root bandit5 4096 Oct 16  2018 .
    drwxr-x--- 22 root bandit5 4096 Oct 16  2018 ..
    -rwxr-x---  1 root bandit5 3663 Oct 16  2018 -file1
    -rwxr-x---  1 root bandit5 3065 Oct 16  2018 .file1
    -rw-r-----  1 root bandit5 2488 Oct 16  2018 -file2
    -rw-r-----  1 root bandit5 1033 Oct 16  2018 .file2
    bandit5@bandit:~$ cat inhere/maybehere07/.file2
    DXjZPULLxYr17uwoI01bNLQbtFemEgo7

