# Level 28

Log into the server as `bandit28` with the password.

> There is a git repository at
> `ssh://bandit28-git@localhost/home/bandit28-git/repo`. The password for the
> user bandit28-git is the same as for the user bandit28.

Same spiel as last level, I create a temp directory and clone the repo into it.

    bandit28@bandit:/tmp/tmp.B64pMkuOcy$ ls repo/
    README.md
    bandit28@bandit:/tmp/tmp.B64pMkuOcy$ cat repo/README.md 
    # Bandit Notes
    Some notes for level29 of bandit.

    ## credentials

    - username: bandit29
    - password: xxxxxxxxxx

I presume that they have deleted the password, so I pull up the logs.

    bandit28@bandit:/tmp/tmp.B64pMkuOcy$ cd repo/
    bandit28@bandit:/tmp/tmp.B64pMkuOcy/repo$ git log
    commit 073c27c130e6ee407e12faad1dd3848a110c4f95
    Author: Morla Porla <morla@overthewire.org>
    Date:   Tue Oct 16 14:00:39 2018 +0200

    fix info leak

    commit 186a1038cc54d1358d42d468cdc8e3cc28a93fcb
    Author: Morla Porla <morla@overthewire.org>
    Date:   Tue Oct 16 14:00:39 2018 +0200

    add missing data

    commit b67405defc6ef44210c53345fc953e6a21338cc7
    Author: Ben Dover <noone@overthewire.org>
    Date:   Tue Oct 16 14:00:39 2018 +0200

    initial commit of README.md

I assume that *fix info leak* is the commit that removes the password, so I run a diff.

    bandit28@bandit:/tmp/tmp.B64pMkuOcy/repo$ git diff HEAD~1
    diff --git a/README.md b/README.md
    index 3f7cee8..5c6457b 100644
    --- a/README.md
    +++ b/README.md
    @@ -4,5 +4,5 @@ Some notes for level29 of bandit.
     ## credentials

    - username: bandit29
    -- password: bbc96594b4e001778eee9975372716b2
    +- password: xxxxxxxxxx

Bingo.
