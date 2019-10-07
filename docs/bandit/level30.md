# Level 30

Log into the server as `bandit30` and the password.

> There is a git repository at
> ssh://bandit30-git@localhost/home/bandit30-git/repo. The password for the
> user bandit30-git is the same as for the user bandit30.

Well, git repositories seem to be quite popular. I do the same spiel again.

    bandit30@bandit:/tmp/tmp.ncBHJehwXo/repo$ ls
    README.md
    bandit30@bandit:/tmp/tmp.ncBHJehwXo/repo$ cat README.md 
    just an epmty file... muahaha

Okay, so there is no information here. I check to see if there is anything in
the logs or data associated with this commit.

	bandit30@bandit:/tmp/tmp.ncBHJehwXo/repo$ git log
	commit 3aa4c239f729b07deb99a52f125893e162daac9e
	Author: Ben Dover <noone@overthewire.org>
	Date:   Tue Oct 16 14:00:44 2018 +0200

		initial commit of README.md
	bandit30@bandit:/tmp/tmp.ncBHJehwXo/repo$ git diff
	bandit30@bandit:/tmp/tmp.ncBHJehwXo/repo$ git sho
	shortlog      show          show-branch
	bandit30@bandit:/tmp/tmp.ncBHJehwXo/repo$ git sho
	shortlog      show          show-branch
	bandit30@bandit:/tmp/tmp.ncBHJehwXo/repo$ git show
	commit 3aa4c239f729b07deb99a52f125893e162daac9e
	Author: Ben Dover <noone@overthewire.org>
	Date:   Tue Oct 16 14:00:44 2018 +0200

		initial commit of README.md

	diff --git a/README.md b/README.md
	new file mode 100644
	index 0000000..029ba42
	--- /dev/null
	+++ b/README.md
	@@ -0,0 +1 @@
	+just an epmty file... muahaha

Negative. Next I check for branches and tags.

	bandit30@bandit:/tmp/tmp.ncBHJehwXo/repo$ git branch -a
	* master
	  remotes/origin/HEAD -> origin/master
	  remotes/origin/master
	bandit30@bandit:/tmp/tmp.ncBHJehwXo/repo$ git tag
	secret

This seems promising — there are no other branches to speak of, but there is a
tag named *secret*. Can I check it out?

	bandit30@bandit:/tmp/tmp.ncBHJehwXo/repo$ git checkout secret
	fatal: reference is not a tree: secret

Seems like I can't. Now, a tag in git is simply a name for a SHA1 hash. So,
what if the hash it points to is the actual secret? I retrieve it.

	bandit30@bandit:/tmp/tmp.ncBHJehwXo/repo$ git show secret
	47e603bb428404d265f59c42920d81e5
	bandit30@bandit:/tmp/tmp.ncBHJehwXo/repo$

Just to be sure, I check if I can log in to the next level with this, and it
works, so this is it.

