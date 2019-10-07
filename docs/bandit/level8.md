# Level 8

Connect to the server using `bandit8` and the password.

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.

    bandit8@bandit:~$ wc data.txt
     1001  1001 33033 data.txt

This file has one thousand lines. Too much to do it by hand. I'm not quite sure, but I check the man page of `uniq`, and it turns out it has an option to do just this.

    bandit8@bandit:~$ sort data.txt | uniq -u
    UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
