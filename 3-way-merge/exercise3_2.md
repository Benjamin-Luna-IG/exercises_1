# The task

You again live in your own branch, this time we will be doing a bit of juggling with branches, to show how lightweight branches are in git.

1. Create a branch called `greeting` and switch to it

```bash
$ git switch -c greeting

Switched to a new branch 'greeting'
```

2. Edit the greeting.txt to contain your favorite greeting

```bash
echo "What's up?" > greeting.txt 
```

3. Add greeting.txt files to the staging area

```bash
git add greeting.txt
```

4. Commit

```bash
$ git commit -m "update to my favorite greeting"

[greeting 2d0263b] update to my favorite greeting
 1 file changed, 1 insertion(+), 1 deletion(-)
```

5. Switch back to the master branch

```bash
$ git switch master 

Switched to branch 'master'
```

6. Create a file README.md with information about this repository
7. Add the README.md file to staging area and make the commit

```bash
$ git add README.md 
$ git commit -m "create the README.md file"

[master 27fe571] create the README.md file
 1 file changed, 3 insertions(+)
 create mode 100644 README.md
```

8. What is the output of `git log --oneline --graph --all`?

```bash
$ git log --oneline --graph --all

* 27fe571 (HEAD -> master) create the README.md file
| * 2d0263b (greeting) update to my favorite greeting
|/  
* 97eaf47 Add content to greeting.txt
* ec9922b Add file greeting.txt
```

9. Diff the branches

```bash
$ git diff master greeting

diff --git a/README.md b/README.md
deleted file mode 100644
index 73d011a..0000000
--- a/README.md
+++ /dev/null
@@ -1,3 +0,0 @@
-# Information
-
-This repository is an example of the merging three different branches to the master branch.
diff --git a/greeting.txt b/greeting.txt
index ce01362..b68722b 100644
--- a/greeting.txt
+++ b/greeting.txt
@@ -1 +1 @@
-hello
+What's up?
```

10. Merge the greeting branch into master

```bash
$ git merge greeting 

Merge made by the 'ort' strategy.
 greeting.txt | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

11. What is the output of `git log --oneline --graph --all` now? Observe the extra merge commit created with the message "Merge branch 'greeting'".

```bash
$ git log --oneline --graph --all

*   76febe4 (HEAD -> master) Merge branch 'greeting'
|\  
| * 2d0263b (greeting) update to my favorite greeting
* | 27fe571 create the README.md file
|/  
* 97eaf47 Add content to greeting.txt
* ec9922b Add file greeting.txt
```
