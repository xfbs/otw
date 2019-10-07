# Level 14

Connect to the server using `bandit14` and the private key.

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

Good old `telnet` should do the trick here.

    bandit14@bandit:~$ telnet localhost 30000
    Trying 127.0.0.1...
    Connected to localhost.
    Escape character is '^]'.
    4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
    Correct!
    BfMYroe26WYalil77FoDi9qh59eK5xNr

    Connection closed by foreign host.
    bandit14@bandit:~$ 

