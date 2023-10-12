# The task

1. _Squash_ the five relevant commits into one and make a good commit message (see Further information).

```bash
$ git log --oneline 

9f9daa2 (HEAD -> master) add the word!
2aba4ac add prime directive
b51a844 most relevant!
603372c Add more relevancy
9a47899 Add relevant fact
faec41c initial file

$ git rebase -i faec41c

[detached HEAD fb2604f] Add relevant fact, a prime directive and a word
 Date: Thu Oct 12 09:57:36 2023 -0700
 1 file changed, 2 insertions(+)
 create mode 100644 file.txt
[detached HEAD a415d49] Add relevant fact, a prime directive and a word
 Date: Thu Oct 12 09:57:36 2023 -0700
 1 file changed, 9 insertions(+)
 create mode 100644 file.txt
Successfully rebased and updated refs/heads/master.
```

Squashed the last 5 commits in the last one and reword the first one to include all the changes in the description.

2. How does `git log` look now?

```bash
$ git log --oneline 

a415d49 (HEAD -> master) Add relevant fact, a prime directive and a word
faec41c initial file
```

3. Clean up the `\n` characters inside `file.txt` without adding to the commit history.

```bash
$ nano file.txt

$ git add .

$ git commit --amend

[master 61e9084] Add relevant fact, a prime directive and a word
 Date: Thu Oct 12 09:57:36 2023 -0700
 1 file changed, 5 insertions(+)
 create mode 100644 file.txt
```