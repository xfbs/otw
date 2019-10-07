# Level 20

Login in as `bandit20` and the password.

> There is a setuid binary in the homedirectory that does the following: it
> makes a connection to localhost on the port you specify as a commandline
> argument. It then reads a line of text from the connection and compares it to
> the password in the previous level (`bandit20`). If the password is correct,
> it will transmit the password for the next level (`bandit21`).

    bandit20@bandit:~$ ls
    suconnect
    bandit20@bandit:~$ ./suconnect 
    Usage: ./suconnect <portnumber>
    This program will connect to the given port on localhost using TCP. If it receives the correct password from the other side, the next password is transmitted back.

What I have to do is use `nc` to setup a TCP server that will send the current password, and the listen for the response. I look at the `nc` man page to see how it is used. I have to start it in the background with `&` so that I can start the binary at the same time.

    bandit20@bandit:~$ cat /etc/bandit_pass/bandit20 | nc -lp 34675 &
    [1] 5398
    bandit20@bandit:~$ ./suconnect 34675
    Read: GbKksEFF4yrVs6il55v6gwY5aVje5f0j
    Password matches, sending next password
    gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr
    [1]+  Done                    cat /etc/bandit_pass/bandit20 | nc -lp 34675
    bandit20@bandit:~$ 

