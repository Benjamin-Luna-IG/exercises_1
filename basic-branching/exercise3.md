# The task

You again live in your own branch, this time we will be doing a bit of juggling with branches, to show how lightweight branches are in git.
Hint: `git switch` will make you switch from one branch to another.

1. Use `git branch` to see the two branches that are relevant for this exercise

```bash
$ git branch
* master
  second-branch
```

2. What branch are you on?

On the `master` branch.

3. Use `git branch mybranch` to create a new branch called _mybranch_

```bash
git branch mybranch
```

4. Use `git branch` again to see the new branch created.

```bash
$ git branch
* master
  mybranch
  second-branch
```

5. Use `git switch mybranch` to switch to your new branch.

```bash
git switch mybranch
```

6. How does the output from `git status` change when you switch between the _master_ and the new branch that you have created?

```bash
$ git status         
On branch master
nothing to commit, working tree clean

$ git switch mybranch
Switched to branch 'mybranch'

$ git status
On branch mybranch
nothing to commit, working tree clean
```

7. How does the workspace change when you change between the two branches?

```bash
$ (master) ls
dummy.txt

$ (mybranch) ls                 
dummy.txt

```

It is the same.

8. Make sure you are on your _mybranch_ branch before you continue.
9. Create a file called `file1.txt` with your name.

```bash
echo "Benjamin" > file1.txt
```

10. `Add` the file and `commit` with this change.

```bash
$ git add file1.txt 
$ git commit -m "create a file with my name"
[mybranch 6de99e8] create a file with my name
 1 file changed, 1 insertion(+)
 create mode 100644 file1.txt
```

11. Use `git log --oneline --graph` to see your branch pointing to the new commit.

```bash
$ git log --oneline --graph
* 6de99e8 (HEAD -> mybranch) create a file with my name
* 87f84e3 (second-branch, master) dummy commit
```

12. Switch back to the branch called _master_.

```bash
$ git switch master 
Switched to branch 'master'
```

13. Use `git log --oneline --graph` and notice how the commit you made on the _mybranch_ branch is missing on the _master_ branch.

```bash
$ git log --oneline --graph
* 87f84e3 (HEAD -> master, second-branch) dummy commit
```

14. Make a new file called `file2.txt` and commit that file.

```bash
$ touch file2.txt
$ git add file2.txt 
$ git commit -m "create a second txt file"
[master 46b8e13] create a second txt file
 1 file changed, 0 insertions(+)
```

15. Use `git log --oneline --graph --all` to see your branch pointing to the new commit, and that the two branches now have different commits on them.

```bash
$ git log --oneline --graph --all
* 46b8e13 (HEAD -> master) create a second txt file
* 87f84e3 (second-branch) dummy commit
```

16. Switch to your branch _mybranch_.

```bash
git switch mybranch 
Switched to branch 'mybranch'
```

17. What happened to your working directory? Can you see your `file2.txt`?

It changed to how it was when I created `file1.txt`.

```bash
$ ls
dummy.txt file1.txt
```

18. Use `git diff mybranch master` to see the difference between the two branches.

```bash
$ git diff mybranch master
diff --git a/file1.txt b/file1.txt
deleted file mode 100644
index e147472..0000000
--- a/file1.txt
+++ /dev/null
@@ -1 +0,0 @@
-Benjamin
diff --git a/file2.txt b/file2.txt
new file mode 100644
index 0000000..e69de29
```