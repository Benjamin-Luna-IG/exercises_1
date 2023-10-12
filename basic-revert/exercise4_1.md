# The task

In this task a few changes snuck in, that we'd like to get out. Our history is public, so we can't just change it. Rather we need to use revert to remove the unwanted changes in a safe way.

1. Use `git log --oneline` to look at the history

```bash
$ git log --oneline

8a12ab2 (HEAD -> master) Overwrite greeting.txt
f50dbff Add content to greeting.txt
d6006dc Add credentials to repository
09fc033 Add file greeting.txt
```

2.  Use `cat` to view the content of `greeting.txt`

```bash
$ cat greeting.txt

This should have been appended to the original content, rather than overwriting it.
```

3.  Use `git revert` on the newest commit, to remove the changes the last commit added

```bash
$ git revert 8a12ab2

[master bee3c13] Revert "Overwrite greeting.txt"
 1 file changed, 1 insertion(+), 1 deletion(-)
```

4.  Use `git log --oneline` to view the history

```bash
$ git log --oneline

bee3c13 (HEAD -> master) Revert "Overwrite greeting.txt"
8a12ab2 Overwrite greeting.txt
f50dbff Add content to greeting.txt
d6006dc Add credentials to repository
09fc033 Add file greeting.txt
```

5.  Did the revert command add or remove a commit?

It adds a new commit reverting the changes.

6.  Use `cat` to view the content of `greeting.txt`

```bash
$ cat greeting.txt

Original file content
```

7.  Use `ls` to see the content of the workspace

```bash
$ ls

credentials.txt greeting.txt
```

8.  Use `git log --oneline` to find the sha of the commit adding credentials to the repository

```bash
$ git log --oneline

bee3c13 (HEAD -> master) Revert "Overwrite greeting.txt"
8a12ab2 Overwrite greeting.txt
f50dbff Add content to greeting.txt
d6006dc Add credentials to repository
09fc033 Add file greeting.txt
```

It is the `d6006dc` sha.

9.  Use `git revert` to revert the commit that added the credentials

```bash
$ git revert d6006dc

[master 0ee2067] Revert "Add credentials to repository"
 1 file changed, 1 deletion(-)
 delete mode 100644 credentials.txt
```

10. Use `git log --oneline` to view the history

```bash
$ git log --oneline

0ee2067 (HEAD -> master) Revert "Add credentials to repository"
bee3c13 Revert "Overwrite greeting.txt"
8a12ab2 Overwrite greeting.txt
f50dbff Add content to greeting.txt
d6006dc Add credentials to repository
09fc033 Add file greeting.txt
```

11. Use `ls` to see the content of the workspace

```bash
$ ls

greeting.txt
```

12. How many commits were added or changed by the last revert?

Only one.

13. Use `git show` with the sha of the commit you reverted to see that the credentials file is still in the history

```bash
$ git show d6006dc

commit d6006dc2bb9861ce95b640d86a27d1dca5d33eeb
Author: git-katas trainer bot <git-katas@example.com>
Date:   Wed Oct 11 17:38:31 2023 -0700

    Add credentials to repository

diff --git a/credentials.txt b/credentials.txt
new file mode 100644
index 0000000..8995708
--- /dev/null
+++ b/credentials.txt
@@ -0,0 +1 @@
+supersecretpassword
```

14. As you have now reverted the credentials file, so it is removed from your working directory, is it also removed from git?

Nope, it is still stored as a blob hashed file that can be reverted.