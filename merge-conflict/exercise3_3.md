# The task

In this kata git cannot figure out how to merge the content added on `merge-conflict-branch1` with the content on `master`.

Both changes need to be in master when you're done.

1. Use `git merge` to bring the changes from `merge-conflict-branch1` on to `master`.

```bash
$ git merge merge-conflict-branch1

Auto-merging file.txt
CONFLICT (add/add): Merge conflict in file.txt
Automatic merge failed; fix conflicts and then commit the result.
```

2. What does `git status` now report.

```bash
$ git status

On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
	both added:      file.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

3. Fix the conflict with your favorite editor.
4. Follow the instructions in `git status` to complete the merge.

```bash
$ git add file.txt 
$ git commit -m "solve the conflicts"

[master 87f2007] solve the conflicts
```

5. What does `git log --oneline --graph` show?

```bash
$ git log --oneline --graph

*   87f2007 (HEAD -> master) solve the conflicts
|\  
| * 825b155 (merge-conflict-branch1) add relevant fact
* | 30038ae add indispensable truth!
|/  
* 5836af3 Add content to greeting.txt
* 248b13d Add file greeting.txt
```
