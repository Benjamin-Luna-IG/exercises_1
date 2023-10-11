1. Use `git status` to see which branch you are on.
```bash
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```
2. What does `git log` look like?
```bash
fatal: your current branch 'master' does not have any commits yet
```
3. Create a file
```bash
touch exercise1.txt
```
4. What does the output from `git status` look like now?
```bash
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	exercise1.txt

nothing added to commit but untracked files present (use "git add" to track)
```
5. `add` the file to the staging area
```bash
git add exercise1.txt 
```
6. How does `git status` look now?
```bash
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   exercise1.txt
```
7. `commit` the file to the repository
```bash
> git commit -m "create an empty file"

[master (root-commit) e512ad7] create an empty file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 exercise1.txt
```
8. How does `git status` look now?
```bash
> git status
On branch master
nothing to commit, working tree clean
```
9. Change the content of the file you created earlier
10. What does `git status` look like now?
```bash
> git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   exercise1.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
11. `add` the file change
```bash
git add exercise1.txt 
```
12. What does `git status` look like now?
```bash
> git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   exercise1.txt
```
13. Change the file again
14. Make a `commit`
```bash
> git commit -m "add two lines to exercise1.txt"
[master dcd146a] add two lines to exercise1.txt
 1 file changed, 1 insertion(+)
```
15. What does the `status` look like now? The `log`?
```bash
> git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   exercise1.txt

no changes added to commit (use "git add" and/or "git commit -a")

> git log --oneline

dcd146a (HEAD -> master) add two lines to exercise1.txt
e512ad7 create an empty file
```
16. Add and commit the newest change
```bash
> git commit -am "add the second line to exercise1.txt"
[master 7a63a3d] add the second line to exercise1.txt
 1 file changed, 1 insertion(+)
```
