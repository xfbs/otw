# Level 29

Log in to the server as `bandit29` and the password.

> There is a git repository at
> ssh://bandit29-git@localhost/home/bandit29-git/repo. The password for the
> user bandit29-git is the same as for the user bandit29.

I do the same spiel again, cloning the repository.

    bandit29@bandit:/tmp/tmp.fXeAddNKnj$ cd repo/
    bandit29@bandit:/tmp/tmp.fXeAddNKnj/repo$ ls
    README.md
    bandit29@bandit:/tmp/tmp.fXeAddNKnj/repo$ cat README.md
    # Bandit Notes
    Some notes for bandit30 of bandit.

    ## credentials

    - username: bandit30
    - password: <no passwords in production!>

    bandit29@bandit:/tmp/tmp.fXeAddNKnj/repo$ git log
    commit 84abedc104bbc0c65cb9eb74eb1d3057753e70f8
    Author: Ben Dover <noone@overthewire.org>
    Date:   Tue Oct 16 14:00:41 2018 +0200

        fix username

    commit 9b19e7d8c1aadf4edcc5b15ba8107329ad6c5650
    Author: Ben Dover <noone@overthewire.org>
    Date:   Tue Oct 16 14:00:41 2018 +0200

        initial commit of README.md

This time the password is nowhere to be found. There is a reference about *production*, so my assumption is that another branch might contain the password.

    bandit29@bandit:/tmp/tmp.fXeAddNKnj/repo$ git branch -a
    * master
      remotes/origin/HEAD -> origin/master
      remotes/origin/dev
      remotes/origin/master
      remotes/origin/sploits-dev
    bandit29@bandit:/tmp/tmp.fXeAddNKnj/repo$

Bingo, there are other branches. I checkout the `dev` branch.

    bandit29@bandit:/tmp/tmp.fXeAddNKnj/repo$ git checkout dev
    Switched to branch 'dev'
    Your branch is up-to-date with 'origin/dev'.
    bandit29@bandit:/tmp/tmp.fXeAddNKnj/repo$ ls
    code  README.md
    bandit29@bandit:/tmp/tmp.fXeAddNKnj/repo$ cat README.md
    # Bandit Notes
    Some notes for bandit30 of bandit.

    ## credentials

    - username: bandit30
    - password: 5b90576bedb2cc04c86a9e924ce42faf

    bandit29@bandit:/tmp/tmp.fXeAddNKnj/repo$

And there it is.
