# The task

After running the setup script, you'll be left with three repositories inside the `exercise` folder.

* A `remote` repository. This is the "remote" repository that would normally exist on your preferred Git repository host, e.g. github.com.
* A `component` repository cloned from `remote`.
* A `product` repository.

Go to the `product` repository.

1. Add component as a submodule of product by running `git submodule add ../remote include`.

I required to set first the next configuration [Source](https://stackoverflow.com/questions/74486167/git-clone-recurse-submodules-throws-error-on-macos-transmission-type-file-n):

```bash
$ git config --global protocol.file.allow always
```

then

```bash
$ git submodule add ../remote include

Cloning into '/Users/bluna/Documents/Intek/Git/ex/git-katas/submodules/exercise/product/include'...
done.
```

2. What does your working directory look like?

```bash
$ ls

include   product.h
```

3. Does `git status` look like you expect?

```bash
$ git status

On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   .gitmodules
	new file:   include
```

I would expect that this new repository is not tracked by the product repo.

4. What if you cd to `include`?

```bash
$ cd include 

$ git status 

On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```

As it is expected.

5. Run `git diff --staged` in `product`. Where can you find the commit id shown in the `+Subproject commit ...` line?

```bash
$ git diff --staged

diff --git a/.gitmodules b/.gitmodules
new file mode 100644
index 0000000..79d5c92
--- /dev/null
+++ b/.gitmodules
@@ -0,0 +1,3 @@
+[submodule "include"]
+       path = include
+       url = ../remote
diff --git a/include b/include
new file mode 160000
index 0000000..7e73771
--- /dev/null
+++ b/include
@@ -0,0 +1 @@
+Subproject commit 7e7377171db2d89c7a791949d2afd48337c863c4
```

You can see the commit if you `cd` to `./include/` and run there `git log --oneline`.

```bash
$ cd include

$ git log --oneline

7e73771 (HEAD -> master, origin/master, origin/HEAD) Touch component header
```

The file is stored in `./.git/modules/include/`.

6. Commit the changes on the `product` repository.

```bash
$ git add .

$ it commit -m "add the submodule remote in include"

[master 00e843e] add the submodule remote in include
 2 files changed, 4 insertions(+)
 create mode 100644 .gitmodules
 create mode 160000 include
```


   Go to the `component` repository.

```bash
$ cd ../component
```

7. Does it know that it is used as a submodule?

No, you update on both sides manually.

8. Make a change to the `component` repository and `git commit` and `git push` it.

```bash
$ echo "small change" > comp_file.txt

$ git add comp_file.txt 

$ git commit -m "add a small change"

[master a78e349] add a small change
 1 file changed, 1 insertion(+)
 create mode 100644 comp_file.txt

$ git push

Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 307 bytes | 307.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To /Users/bluna/Documents/Intek/Git/ex/git-katas/submodules/exercise/remote
   7e73771..a78e349  master -> master
```

   Go to the `product` repository.

```bash
cd ../product
```

9. Does `git status` or `git submodule foreach 'git status'` tell you anything about this new commit?

```bash
$ git status

On branch master
nothing to commit, working tree clean

$ git submodule foreach 'git status'

Entering 'include'
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```

10. Go to the `include` directory and `git pull` the latest version.

```bash
$ cd include 

$ git pull

remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 287 bytes | 287.00 KiB/s, done.
From /Users/bluna/Documents/Intek/Git/ex/git-katas/submodules/exercise/remote
   7e73771..a78e349  master     -> origin/master
Updating 7e73771..a78e349
Fast-forward
 comp_file.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 comp_file.txt
```

11. Verify that the change from the `component` repository is available in `include`.

```bash
$ cat comp_file.txt

small change
```

12. Go to the `product` directory. What is the status now in your product repository? Also examine with `git diff`.

```bash
$ git status

On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   include (new commits)

no changes added to commit (use "git add" and/or "git commit -a")

$ git diff

diff --git a/include b/include
index 7e73771..a78e349 160000
--- a/include
+++ b/include
@@ -1 +1 @@
-Subproject commit 7e7377171db2d89c7a791949d2afd48337c863c4
+Subproject commit a78e3494e6a040854ba73644b2c91cfb6386adfc
```

13. Go to your `include` folder. Make a change and `push` it back to its origin.

```bash
$ cd include

$ echo "second small change" >> comp_file.txt

$ git add comp_file.txt 

$ git commit -m "add a second small change"
[master c25bd73] add a second small change
 1 file changed, 1 insertion(+)
```

 > Go to the `exercise` directory. We will make a clone of product to illustrate how submodules in a clone must be initialized.

14. Run `git clone product product_alpha`.

```bash
$ git clone product product_alpha

Cloning into 'product_alpha'...
done.
```

15. Go to `product_alpha` directory, how does your working directory look, what does the log say and what is in the `include` directory?

```bash
$ cd product_alpha 

$ ls

include   product.h

$ git log --oneline 

00e843e (HEAD -> master, origin/master, origin/HEAD) add the submodule remote in include
0d9180c Touch product header

$ ls include
```

`include` is empty.

16. Run `git submodule init`, what does your `include` dir look like?

```bash
$ git submodule init

Submodule 'include' (/Users/bluna/Documents/Intek/Git/ex/git-katas/submodules/exercise/remote) registered for path 'include'

$ ls include
```

`include` is still empty.

17. Run `git submodule update`, what does your `include` dir look like now?
> (* Note: you can combine the previous two steps by doing `git submodule update --init`)

```bash
$ git submodule update

Cloning into '/Users/bluna/Documents/Intek/Git/ex/git-katas/submodules/exercise/product_alpha/include'...
done.
Submodule path 'include': checked out '7e7377171db2d89c7a791949d2afd48337c863c4'

$ ls include

component.h
```

18. Is the latest change from `component` available in include?

No, it does not have the file `comp_file.txt`.

>    Go to the `product` repository.

```bash
$ cd ../product
```

19. Commit the changes on the `product` repository. Please forget to push the changes for now ;-)

```bash
$ git commit -m "update the submodule"

[master 086279c] update the submodule
 1 file changed, 1 insertion(+), 1 deletion(-)
```

> Go to the `product_alpha` repository. We'll ensure that we have the latest changes from product.

```bash
$ cd ../product_alpha 
```

20. Run `git submodule update`.

```bash
$ git submodule update 
```

21. Is the latest change from `component` available in `include`?

```bash
$ ls include 

component.h
```

Not yet.

22. Examine the output of `git submodule status`. Compare the commit id with the `component` repository.

```bash
$ git submodule status

 7e7377171db2d89c7a791949d2afd48337c863c4 include (7e73771)
```

It is not the last one (`a78e349`).

23. Run `git submodule update --remote`.

```bash
$ git submodule update --remote

Submodule path 'include': checked out 'a78e3494e6a040854ba73644b2c91cfb6386adfc'
```

24. Is the latest change from `component` available in include?

Yes

```bash
$ ls include

comp_file.txt component.h
```

25. Examine the output of `git submodule status`. Compare the commit id with the `component` repository.

```bash
$ git submodule status 

+a78e3494e6a040854ba73644b2c91cfb6386adfc include (heads/master)
```
It is the same commit id.