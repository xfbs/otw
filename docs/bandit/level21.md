# Level 21

Connect to the server with `bandit21` and the password.

> A program is running automatically at regular intervals from cron, the
> time-based job scheduler. Look in /etc/cron.d/ for the configuration and see
> what command is being executed.

I try to find the cron job file, because the `crontab` utility doesn't work.

    bandit21@bandit:~$ cat /etc/cron.d/cronjob_bandit22
    @reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
    * * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null

There is some bash script involved, so I look at that.

    bandit21@bandit:~$ cat /usr/bin/cronjob_bandit22.sh 
    #!/bin/bash
    chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
    cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv

The `chmod` tells me that I can read this file. So I do.

    bandit21@bandit:~$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
    Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI

