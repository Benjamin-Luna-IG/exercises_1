# The task
You are working on a project that involves generated files.  Say you are compiling C files into object files. Before checking out a new branch you want to start clean

1. Explore the directory with `ls -R`. There is a lot going on.  Code files, temp files, object files,..  Let's clean up!

```bash
$ ls -R

README.txt  README.txt~ obj         src

./obj:
a.out   myapp.o mylib.a mylib.o

./src:
myapp.c    myapp.c~   myapp.h    mylib.c    oldfile.c~
```

2. Just to be safe, do a dry run and execute the clean command with the ` -n` option

```bash
$ git clean -n

Would remove README.txt~
Would remove src/myapp.c~
Would remove src/mylib.c
Would remove src/oldfile.c~
```

3. Oh noes!  there's a `.c` file that would have been deleted!
4. Add `src/mylib.c` to the staging area. don't commit it.

```bash
$ git add src/mylib.c

$ git status

On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   src/mylib.c

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	README.txt~
	obj/
	src/myapp.c~
	src/oldfile.c~
```

5. Run the clean command with the ` -n` option. Notice that mylib.c will not be deleted. Also notice that the files in the obj directory are not listed

```bash
$ git clean -n       

Would remove README.txt~
Would remove src/myapp.c~
Would remove src/oldfile.c~
```

6. Run the clean command with the ` -n -d ` option.

```bash
$ git clean -n -d

Would remove README.txt~
Would remove obj/
Would remove src/myapp.c~
Would remove src/oldfile.c~
```

7. Looks good! clean the repo ` -f -d `

```bash
$ git clean -f -d

Removing README.txt~
Removing obj/
Removing src/myapp.c~
Removing src/oldfile.c~

$ git status

On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   src/mylib.c
```