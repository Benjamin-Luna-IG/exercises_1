# Task

1. Explore the repo and the history so you know what happened

```bash
$ git log --oneline

4585963 (HEAD -> master) I forgot a semicolon
7da8624 Test for feature hello world
8634426 Add doc - step 3
55a3c25 Add doc - step 2
c66cfd2 Add doc - step 1
a5110b2 important secret
da3f8e2 debugging
9dc1b8d Really made the thingy done
71f6972 Finished HW feature
12909fe Helo Volrd feature
9e9b981 (tag: v0.0, origin/master) Initial commit
```

2. Use `git rebase --interactive v0.0` to let you edit the "recipe" for the entire feature development.

```bash
$ git rebase --interactive v0.0

[detached HEAD 3f1e273] add feature Hello World
 Date: Thu Oct 12 10:51:34 2023 -0700
 1 file changed, 1 insertion(+)
 create mode 100644 hello.code
[detached HEAD 36113b1] add feature Hello World
 Date: Thu Oct 12 10:51:34 2023 -0700
 2 files changed, 2 insertions(+)
 create mode 100644 hello.code
 create mode 100644 other.code
[detached HEAD e4d3ea1] add file with secret text
 Date: Thu Oct 12 10:51:34 2023 -0700
 1 file changed, 1 insertion(+)
 create mode 100644 private.secret
[detached HEAD 56c48a0] create test fot the Hello World feature
 Date: Thu Oct 12 10:51:34 2023 -0700
 1 file changed, 1 insertion(+)
 create mode 100644 hello.test
[detached HEAD 50c152e] create test fot the Hello World feature
 Date: Thu Oct 12 10:51:34 2023 -0700
 1 file changed, 1 insertion(+)
 create mode 100644 hello.test
Successfully rebased and updated refs/heads/master.
```

3. Clean up the history such that it actually makes sense. Try to use as many of the rebase "features" (e.g. reword, squash, fixup, drop) as possible. You decide yourself if you want to rewrite the whole thing in one go, or apply a few changes first, then run a new `git rebase --interactive v0.0` to keep cleaning.

```bash
$ git log --oneline

50c152e (HEAD -> master) create test fot the Hello World feature
2ffa211 Add doc - step 1
e4d3ea1 add file with secret text
36113b1 add feature Hello World
9e9b981 (tag: v0.0, origin/master) Initial commit
```

I forgot to reword the `2ffa211` commit.

```bash
$ git rebase --interactive v0.0

[detached HEAD 73ccd18] Add documentation
 Date: Thu Oct 12 10:51:34 2023 -0700
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
Successfully rebased and updated refs/heads/master.

$ git log --oneline

2a80f0a (HEAD -> master) create test fot the Hello World feature
73ccd18 Add documentation
e4d3ea1 add file with secret text
36113b1 add feature Hello World
9e9b981 (tag: v0.0, origin/master) Initial commit
```