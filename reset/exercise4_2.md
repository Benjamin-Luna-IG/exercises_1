# Task

1. How does your working directory look like?

```bash
$ ls

1.txt  10.txt 2.txt  3.txt  4.txt  5.txt  6.txt  7.txt  8.txt  9.txt
```

2. What does your log look like? What does your stage look like?

```bash
$ git log --oneline

6170dea (HEAD -> master) 10
63964df 9
a61ba40 8
9d088c6 7
5b9be7e 6
81df136 5
238e23f 4
0367192 3
9680664 2
393120b 1

$ git diff --staged
```

3. Try to run `git reset --soft HEAD~1`

```bash
git reset --soft HEAD~1
```

4. What happens to your working directory, your log and your stage?

```bash
$ ls

1.txt  10.txt 2.txt  3.txt  4.txt  5.txt  6.txt  7.txt  8.txt  9.txt

$ git log --oneline

63964df (HEAD -> master) 9
a61ba40 8
9d088c6 7
5b9be7e 6
81df136 5
238e23f 4
0367192 3
9680664 2
393120b 1

$ git diff --staged  

diff --git a/10.txt b/10.txt
new file mode 100644
index 0000000..f599e28
--- /dev/null
+++ b/10.txt
@@ -0,0 +1 @@
+10
```

5. Run `git reset --mixed HEAD~1`

```bash
git reset --mixed HEAD~1
```

6. What happens to your working directory, your log and your stage?

```bash
$ ls

1.txt  10.txt 2.txt  3.txt  4.txt  5.txt  6.txt  7.txt  8.txt  9.txt

$ git log --oneline

a61ba40 (HEAD -> master) 8
9d088c6 7
5b9be7e 6
81df136 5
238e23f 4
0367192 3
9680664 2
393120b 1

$ git diff --staged  

$ git status

git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	10.txt
	9.txt

nothing added to commit but untracked files present (use "git add" to track)
```

7. Run `git reset --hard HEAD~1`

```bash
$ git reset --hard HEAD~1

HEAD is now at 9d088c6 7
```

8. What happens to your working directory, your log and your stage?

```bash
$ ls

1.txt  10.txt 2.txt  3.txt  4.txt  5.txt  6.txt  7.txt  9.txt

$ git log --oneline

9d088c6 (HEAD -> master) 7
5b9be7e 6
81df136 5
238e23f 4
0367192 3
9680664 2
393120b 1

$ git diff --staged 

$ git status

On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	10.txt
	9.txt

nothing added to commit but untracked files present (use "git add" to track)
```

9. Now try to use `git revert HEAD~1`

```bash
$ git revert HEAD~1

git revert HEAD~1
[master 2ce58c8] Revert "6"
 1 file changed, 1 deletion(-)
 delete mode 100644 6.txt
```

10. What happens to your working directory, your log and your stage?

```bash
$ ls

1.txt  10.txt 2.txt  3.txt  4.txt  5.txt  7.txt  9.txt

$ git log --oneline

2ce58c8 (HEAD -> master) Revert "6"
9d088c6 7
5b9be7e 6
81df136 5
238e23f 4
0367192 3
9680664 2
393120b 1

$ git diff --staged 

$ git status

On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	10.txt
	9.txt

nothing added to commit but untracked files present (use "git add" to track)
```
