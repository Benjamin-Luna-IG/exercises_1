# The task

1. Run `git branch` to see the two branches present

```bash
$ git branch

  Mergesort-Impl
* master
```

2. Merge `Mergesort-Impl` into `master`

```bash
$ git merge Mergesort-Impl 

Auto-merging mergesort.py
CONFLICT (content): Merge conflict in mergesort.py
Automatic merge failed; fix conflicts and then commit the result.
```

3. Either:
   1. Solve the merge conflict with your favorite editor and finish the merge (`git status` will tell you what to do), **or**
   2. Use `git mergetool --tool=emerge` (for emacs fans) or `git mergetool --tool=vimdiff` (for vim fans) and finish the merge (`git status` will tell you what to do)

```bash
$ git status

On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
	both modified:   mergesort.py

no changes added to commit (use "git add" and/or "git commit -a")

$ code mergesort.py 
$ git add mergesort.py 
$ git commit -m "solve the merging conflicts"

[master 42292a9] solve the merging conflicts

$ git log --oneline --graph --all

*   42292a9 (HEAD -> master) solve the merging conflicts
|\  
| * 5f4161f (Mergesort-Impl) Mergesort implemented on feature branch
* | 89d1eb2 Mergesort implemented on master
|/  
* cba82be Fake it till you make it - Faking mergesort using python .sort() method

```
