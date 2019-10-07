# Level 15

Login to the server using `bandit14` and the private key.

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

Apparently `s_client` from openSSL can do something like this, so I pull out the man page and figure out how to use it.

    bandit14@bandit:~$ openssl s_client -connect localhost:30001 -quiet
    depth=0 CN = localhost
    verify error:num=18:self signed certificate
    verify return:1
    depth=0 CN = localhost
    verify return:1
    BfMYroe26WYalil77FoDi9qh59eK5xNr
    Correct!
    cluFn7wTiGryunymYOu4RcffSxQluehd

    bandit14@bandit:~$ 

