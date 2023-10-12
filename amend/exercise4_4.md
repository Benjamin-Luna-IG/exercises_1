# The task

1. What does `git status` tell us?

```bash
$ git status

On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	bar.txt

nothing added to commit but untracked files present (use "git add" to track)
```

2. What does `git log -p` tell us?

```bash
$ git log -p

commit 1f075f7eb8906c180c06650e0e95cf5e6e4d49be (HEAD -> master)
Author: Benjamin Luna <benjamin_lunaveronico@hotmail.com>
Date:   Thu Oct 12 09:35:22 2023 -0700

    feature 73

diff --git a/foo.txt b/foo.txt
new file mode 100644
index 0000000..257cc56
--- /dev/null
+++ b/foo.txt
@@ -0,0 +1 @@
+foo
```

3. Stage the addition of bar.txt

```bash
git add bar.txt
```

4. Run `git commit --amend`

```bash
$ git commit --amend

[master 91271ab] feature 73
 Date: Thu Oct 12 09:35:22 2023 -0700
 2 files changed, 2 insertions(+)
 create mode 100644 bar.txt
 create mode 100644 foo.txt
```

5. What happened? What does `git log -p` tell us?

```bash
$ git log -p

commit 91271ab83d9fd2c77f3a2599ba69ad7ab5fd4960 (HEAD -> master)
Author: Benjamin Luna <benjamin_lunaveronico@hotmail.com>
Date:   Thu Oct 12 09:35:22 2023 -0700

    feature 73

diff --git a/bar.txt b/bar.txt
new file mode 100644
index 0000000..5716ca5
--- /dev/null
+++ b/bar.txt
@@ -0,0 +1 @@
+bar
diff --git a/foo.txt b/foo.txt
new file mode 100644
index 0000000..257cc56
--- /dev/null
+++ b/foo.txt
@@ -0,0 +1 @@
+foo
```

6. What happens if you run `git commit --amend` again?

```bash
$ git commit --amend

[master 3022bf7] feature 73
 Date: Thu Oct 12 09:35:22 2023 -0700
 2 files changed, 2 insertions(+)
 create mode 100644 bar.txt
 create mode 100644 foo.txt
```


Repeat the process, but nothing changes since we have changed nothing since the commit.