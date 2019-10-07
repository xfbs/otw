# Level 22

Connect to the server with `bandit22` and the password.

> A program is running automatically at regular intervals from cron, the
> time-based job scheduler. Look in /etc/cron.d/ for the configuration and see
> what command is being executed.

Again, I see what this cron job looks like.

    bandit22@bandit:~$ cat /etc/cron.d/cronjob_bandit23
    @reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
    * * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null

I take a look at this bash script.

    bandit22@bandit:~$ cat /usr/bin/cronjob_bandit23.sh
    #!/bin/bash

    myname=$(whoami)
    mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

    echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

    cat /etc/bandit_pass/$myname > /tmp/$mytarget

This is very easy, I simply have to re-run this with *myname* set to `bandit23` to get the target name.

    bandit22@bandit:~$ myname=bandit23
    bandit22@bandit:~$ mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)
    bandit22@bandit:~$ cat /tmp/$mytarget
    jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n
    bandit22@bandit:~$ 

