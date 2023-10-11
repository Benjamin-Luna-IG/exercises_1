# The task

You live in your own repository. There is a file called `file.txt`.

1. What's the content of `file.txt`?

```bash
> cat file.txt 
1
```

2. Overwrite the content in `file.txt`: `echo 2 > file.txt` to change the state of your file in the working directory (or `sc file.txt '2'` in PowerShell)
```bash
echo 2 > file.txt
```
3. What does `git diff` tell you?
```bash
$ git diff
diff --git a/file.txt b/file.txt
index d00491f..0cfbf08 100644
--- a/file.txt
+++ b/file.txt
@@ -1 +1 @@
-1
+2
```
4. What does `git diff --staged` tell you? why is this blank?

It is blank because we have not staged anything yet and this instruction compares the staged changes with the previous commit (HEAD).

5. Run `git add file.txt` to stage your changes from the working directory.

```bash
git add file.txt
```

6. What does `git diff` tell you?

This time it is blank because we have already staged the changes.

7. What does `git diff --staged` tell you?

```bash
$ git diff --staged
diff --git a/file.txt b/file.txt
index d00491f..0cfbf08 100644
--- a/file.txt
+++ b/file.txt
@@ -1 +1 @@
-1
+2
```

8. Overwrite the content in `file.txt`: `echo 3 > file.txt` to change the state of your file in the working directory (or `sc file.txt '3'` in PowerShell).

```bash
echo 3 > file.txt
```

9. What does `git diff` tell you?

```bash
$ git diff
diff --git a/file.txt b/file.txt
index 0cfbf08..00750ed 100644
--- a/file.txt
+++ b/file.txt
@@ -1 +1 @@
-2
+3
```

10. What does `git diff --staged` tell you?

```bash
$ git diff --staged
diff --git a/file.txt b/file.txt
index d00491f..0cfbf08 100644
--- a/file.txt
+++ b/file.txt
@@ -1 +1 @@
-1
+2
```

11. Explain what is happening

`git diff` is comparing the working directory with the staging area, and `git diff --staged` is comparing the staging area with respect to the last commit (HEAD).

12. Run `git status` and observe that `file.txt` are present twice in the output.

```bash
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   file.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   file.txt
```

13. Run `git restore --staged file.txt` to unstage the change

```bash
git restore --staged file.txt
```

14. What does `git status` tell you now?

```bash
$ git status                   
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   file.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

15. Stage the change and make a commit

```bash
$ git add file.txt 
$ git commit -m "update the number in file.txt to 3"
[master 117cdbb] update the number in file.txt to 3
 1 file changed, 1 insertion(+), 1 deletion(-)
```

16. What does the log look like?

```bash
$  git log --oneline

117cdbb (HEAD -> master) update the number in file.txt to 3
490a466 1
```

17. Overwrite the content in `file.txt`: `echo 4 > file.txt` (or `sc file.txt '4'` in PowerShell)

```bash
echo 4 > file.txt
```

18. What is the content of `file.txt`?

```bash
$ cat file.txt 
4
```

19. What does `git status` tell us?

```bash
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   file.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

20. Run `git restore file.txt`

```bash
git restore file.txt 
```

21. What is the content of `file.txt`?

```bash
$ cat file.txt 
3
```

22. What does `git status` tell us?

```bash
$ git status
On branch master
nothing to commit, working tree clean
```
