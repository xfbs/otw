# Level 9

Login to the server using `bandit9` and the password.

The password for the next level is stored in the file data.txt in one of the few human-readable strings, beginning with several ‘=’ characters.

    bandit9@bandit:~$ vim data.txt

I inspect the data in `vim`. It's a binary garbled mess. No newlines. I could use `grep` to do it, since I know that it's going to start with some equal signs, and the password will be alphanumerical.

It's not straightforward, but `grep` does turn out to have exactly the options I need.

* `-o` only show matching part.
* `-b` show byte offset in file.
* `--binary-files=text` treat binary files as if they were text.
* `-E` use extended regex.
* `"=[= a-zA-Z0-9]{20,99}"` match on equals sign, followed by at least 20 characters composed of equal signs, spaces, or alphanumerical characters.

    bandit9@bandit:~$ grep -ob --binary-files=text -E "=[= a-zA-Z0-9]{20,99}" data.txt
    16190:========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
