# Task

Reorder the history such that it actually makes sense - add the files in the order that matches their name.

1. Use `git log --oneline --graph` to view the commits

```bash
$ git log --oneline --graph

* 2b0d286 (HEAD -> master) file7
* b671bf8 file6
* aebe460 file2
* 6e5b228 file5
* 5cc2fce file4
* e56434d file3
* b8d7318 file8
* 0c00099 file9
* 6ca46ee file1
* f8dabed (tag: START, origin/master) Initial commit
```

2. Also try `git reflog` to view the commits. `git reflog` defaults to `git reflog show` and this is an alias for `git log -g --abbrev-commit --pretty=oneline`

```bash
$ git reflog

2b0d286 (HEAD -> master) HEAD@{0}: commit: file7
b671bf8 HEAD@{1}: commit: file6
aebe460 HEAD@{2}: commit: file2
6e5b228 HEAD@{3}: commit: file5
5cc2fce HEAD@{4}: commit: file4
e56434d HEAD@{5}: commit: file3
b8d7318 HEAD@{6}: commit: file8
0c00099 HEAD@{7}: commit: file9
6ca46ee HEAD@{8}: commit: file1
f8dabed (tag: START, origin/master) HEAD@{9}: commit (initial): Initial commit
```

3. Use `git rebase -i <after-this-commit>` to reorder the commits. There are commments in the file you edit that explain the commands available.

```bash
$ git rebase -i 6ca46ee
    
Successfully rebased and updated refs/heads/master.
```

4. Use `git log --oneline --graph` to view the result

```bash
$ git log --oneline --graph

* 931a66a (HEAD -> master) file9
* c136061 file8
* 2606f02 file7
* eeb98f9 file6
* f80294e file5
* 6cbe5b0 file4
* 2a31b3f file3
* 4e36286 file2
* 6ca46ee file1
* f8dabed (tag: START, origin/master) Initial commit
```