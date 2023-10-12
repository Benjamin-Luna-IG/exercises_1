# The task

You again live in your own branch, this time we will be doing a bit of juggling with branches, to show how lightweight branches are in git.

1. Which branches exist?

```bash
$ git branch 

* master
  uppercase
```

2. Look at the log for the master branch

```bash
$ git log --oneline 

82051a4 (HEAD -> master) Add readme
2b5aefc Add content to greeting.txt
3eac3a8 Add file greeting.txt
```

3. Switch to the uppercase branch

```bash
$ git switch uppercase 

Switched to branch 'uppercase'
```

4. How does the log compare to the log on the master branch?

```bash
$ git log --oneline 

0b9c1c8 (HEAD -> uppercase) Change greeting to uppercase
2b5aefc Add content to greeting.txt
3eac3a8 Add file greeting.txt
```

5. Rebase your uppercase branch with the master (`git rebase master`)

```bash
$ git rebase master

Successfully rebased and updated refs/heads/uppercase.
```

6. What did just happen? Draw it!

```bash
$ git log --oneline --graph --all

* 80d0e75 (HEAD -> uppercase) Change greeting to uppercase
* 82051a4 (master) Add readme
* 2b5aefc Add content to greeting.txt
* 3eac3a8 Add file greeting.txt
```

The `uppercase` branch updated its contents and instead of start in the `2b5aefc` commit, now it begins at the end of the `master` branch.

7. Now switch to the master branch

```bash
$ git switch master 

Switched to branch 'master'
```

8. Merge uppercase into master

```bash
$ git merge uppercase

Updating 82051a4..80d0e75
Fast-forward
 greeting.txt | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

9. What does the log look like now?

```bash
$ git log --oneline --graph --all

* 80d0e75 (HEAD -> master, uppercase) Change greeting to uppercase
* 82051a4 Add readme
* 2b5aefc Add content to greeting.txt
* 3eac3a8 Add file greeting.txt
```
