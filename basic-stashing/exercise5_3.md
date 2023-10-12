# The task

You are working on your project. You've staged some work and have some unstaged work as well.
Suddenly, you're made aware that a bug has made it to production. You'll stash your work, fix the bug and get back to your original work.

1. Explore the repo
   1. What work do you have in the working directory?

    ```bash
    $ git diff

    diff --git a/file.txt b/file.txt
    index dbdf3fe..c179bba 100644
    --- a/file.txt
    +++ b/file.txt
    @@ -1,2 +1,3 @@
    Initial content of the file
    some changes I made and staged
    +some changes I made and did not stage yet
    diff --git a/fix.txt b/fix.txt
    index e69de29..7095e9d 100644
    --- a/fix.txt
    +++ b/fix.txt
    @@ -0,0 +1 @@
    +changes I did not stage
    ```

   2. What work do you have staged ?

    ```bash
    $ git diff --staged

    diff --git a/file.txt b/file.txt
    index 746e5bd..dbdf3fe 100644
    --- a/file.txt
    +++ b/file.txt
    @@ -1 +1,2 @@
    Initial content of the file
    +some changes I made and staged
    ```

   3. What does the commit log look like ?

    ```bash
    $ git log --oneline

    d1a3ddb (HEAD -> master) add bug.txt
    da85eb8 Initial commit
    ```

   >*Notice that file.txt has some staged changes (i.e. changes in the index) and unstaged changes (changes in the working directory)*
2. Use `git stash` to stash your current work.

```bash
$ git stash

Saved working directory and index state WIP on master: d1a3ddb add bug.txt
```

   1. Now, what work do you have in the working directory?
   
   ```bash
   $ git diff
   ```

   No changes with respect to HEAD.
   
   2. What work do you have staged ?

```bash
    $ git diff --staged
```

   No changes with respect to HEAD.

   3. What does the commit log look like ?

```bash
    $ git log --oneline

    d1a3ddb (HEAD -> master) add bug.txt
    da85eb8 Initial commit
```

   4. What does the stash list look like ?

```bash
$ git stash list

stash@{0}: WIP on master: d1a3ddb add bug.txt
```

3. Fix the typos in bug.txt on master and commit your changes.

```bash
$ nano bug.txt

$ git add bug.txt

$ git commit -m "fix the typos in bug.txt"

[master 8799ea5] fix the typos in bug.txt
 1 file changed, 1 insertion(+), 1 deletion(-)
```

4. Now to get back to your work, apply the stash to master.

```bash
$ git stash apply

On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   file.txt
	modified:   fix.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

   1. What work do you have in the working directory?

```bash
$ git diff

diff --git a/file.txt b/file.txt
index 746e5bd..c179bba 100644
--- a/file.txt
+++ b/file.txt
@@ -1 +1,3 @@
 Initial content of the file
+some changes I made and staged
+some changes I made and did not stage yet
diff --git a/fix.txt b/fix.txt
index e69de29..7095e9d 100644
--- a/fix.txt
+++ b/fix.txt
@@ -0,0 +1 @@
+changes I did not stage
```

   2. What work do you have staged ?

```bash
$ git diff --staged
```

   >*Oops. All our changes are unstaged now. This may be undesirable and unexpected*
5. Undo our changes with `git reset --hard HEAD`. This is an unsafe command as it will remove files from your index and working directory permanently, but we have our changes safely stashed so we're ok. Review the [reset](reset/README.md) kata if you're unsure of what happens here.

```bash
$ git reset --hard HEAD

HEAD is now at 8799ea5 fix the typos in bug.txt
```

6. Apply the stash to master with the `--index` option.

```bash
$ git stash apply stash@{0} --index

On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   file.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   file.txt
	modified:   fix.txt
```

   1. What work do you have in the working directory?

```bash
$ git diff

diff --git a/file.txt b/file.txt
index dbdf3fe..c179bba 100644
--- a/file.txt
+++ b/file.txt
@@ -1,2 +1,3 @@
 Initial content of the file
 some changes I made and staged
+some changes I made and did not stage yet
diff --git a/fix.txt b/fix.txt
index e69de29..7095e9d 100644
--- a/fix.txt
+++ b/fix.txt
@@ -0,0 +1 @@
+changes I did not stage
```

   2. What work do you have staged ?

```bash
$ git diff --staged

diff --git a/file.txt b/file.txt
index 746e5bd..dbdf3fe 100644
--- a/file.txt
+++ b/file.txt
@@ -1 +1,2 @@
 Initial content of the file
+some changes I made and staged
```

   >*Ok, back to where we were!*
7. We won't need the stash anymore. Drop it.

```bash
$ git stash drop

Dropped refs/stash@{0} (ee7e431fdff6e718c240fb7b4a2dd52aac20a34c)
```

   1. What does the stash list look like ?

```bash
$ git stash list
```

   2. What does the commit log look like ?

```bash
$ git log --oneline 

8799ea5 (HEAD -> master) fix the typos in bug.txt
d1a3ddb add bug.txt
da85eb8 Initial commit
```