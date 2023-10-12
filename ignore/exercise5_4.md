# The task

1. Create a file with the name `foo.s`

```bash
$ touch foo.s
```

2. What is the output of `git status`?

```bash
$ git status

On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	file1.txt
	foo.s

nothing added to commit but untracked files present (use "git add" to track)
```

3. Create a `.gitignore` file in your working directory containing `*.s`

```bash
echo "*.s" > .gitignore
```

4. What is the output of `git status`?

```bash
$ git status    

On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	.gitignore
	file1.txt

nothing added to commit but untracked files present (use "git add" to track)
```

5. Commit the `.gitignore` file

```bash
$ git add .gitignore 
$ git commit -m "add the .gitignore file"

[master (root-commit) 491da28] add the .gitignore file
 1 file changed, 1 insertion(+)
 create mode 100644 .gitignore
```

6. Commit `file1.txt`

```bash
$ git add file1.txt 
$ git commit -m "add file1.txt"

[master 539d541] add file1.txt
 1 file changed, 1 insertion(+)
 create mode 100644 file1.txt
```

7. Add `txt` files to `.gitignore` by adding a line in the file containing `*.txt`

```bash
$ echo "*.txt" >> .gitignore 
```

8. What does `git status` tell us?

```bash
$ git status

On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   .gitignore

no changes added to commit (use "git add" and/or "git commit -a")
```

9. Change `file1.txt`

```bash
$ echo "appended text" >> file1.txt
```

10. What does `git status` tell us? Why was the file tracked even though the `txt` extension is in the ignore file?

```bash
$ git status

On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   .gitignore
	modified:   file1.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

Because it was already being tracked by a commit before we add the wildcard `*.txt` to the .gitignore file.

11. Make another text file `file2.txt` in the repository, what does `git status` look like now? Why is it not tracked?

```bash
$ echo "second file text" > file2.txt

$ git status

On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   .gitignore
	modified:   file1.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

Because it was not previously tracked by a commit before we added the `*.txt` wildcard to the .gitignore file.

12. Stage the removal of `file1.txt` with the command `git rm --cached`

```bash
$ git rm --cached file1.txt

rm 'file1.txt'
```

13. What does `git status` say?

```bash
$ git status

On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	deleted:    file1.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   .gitignore

```

14. Create a new file called `file3.txt` and add the line `!file3.txt` to `.gitignore`. (See _note_ below)

```bash
$ touch file3.txt

$ echo "\!file3.txt" >> .gitignore 

```

15. What does `git status` say? Can you think of a use-case for keeping track of a file although the extension is ignored?

```bash
$ git status

On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	deleted:    file1.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   .gitignore

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	file3.txt
```

I do not know any real-life scenario where you need it.
