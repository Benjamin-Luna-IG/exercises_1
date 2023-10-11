# The task

You again live in your own branch, this time we will be doing a bit of juggling with branches, to show how lightweight branches are in git.

1. Create a (feature)branch called `feature/uppercase` (yes, `feature/uppercase` is a perfectly legal branch name, and a common convention).
2. Switch to this branch

```bash
git switch -c feature/uppercase
```

3. What is the output of `git status`?

```bash
$ git status 

On branch feature/uppercase
nothing to commit, working tree clean
```

4. Edit the `greeting.txt`` to contain an uppercase greeting
5. Add `greeting.txt` files to staging area and commit

```bash
$ git add greeting.txt 
$ git commit -m "uppercase the greeting"

[feature/uppercase 3082cc9] uppercase the greeting
 1 file changed, 1 insertion(+), 1 deletion(-)
```

6. What is the output of `git branch`?

```bash
$ git branch

* feature/uppercase
  master
```

7. What is the output of `git log --oneline --graph --all`

```bash
$ git log --oneline --graph --all

* 3082cc9 (HEAD -> feature/uppercase) uppercase the greeting
* 25c6375 (master) Add content to greeting.txt
* ca53f35 Add file greeting.txt
```

8. Switch to the `master` branch

```bash
$ git switch master 

Switched to branch 'master'
```

9. Use `cat` to see the contents of the greetings

```bash
$ cat greeting.txt 

hello
```

10. Diff the branches

```bash
$ git diff feature/uppercase master

diff --git a/greeting.txt b/greeting.txt
index e965047..ce01362 100644
--- a/greeting.txt
+++ b/greeting.txt
@@ -1 +1 @@
-Hello
+hello
```

11. Merge the branches

```bash
$ git merge feature/uppercase 

Updating 25c6375..3082cc9
Fast-forward
 greeting.txt | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

12. Use `cat` to see the contents of the greetings

```bash
$ cat greeting.txt      

Hello
```

13. Delete the uppercase branch

```bash
$ git branch -d feature/uppercase 

Deleted branch feature/uppercase (was 3082cc9).
```