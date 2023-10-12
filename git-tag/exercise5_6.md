# The task

For simplicity, we will just work with the master branch in this kata. A couple
of tags are already created.

1. See which tags that were created.

```bash
$ git tag

dummy
dummy2

$ git log --oneline

5d54e89 (HEAD -> master, tag: dummy2) adding more content to dummy.txt
7973d75 (tag: dummy) dummy commit
```

2. Make a new commit, and introduce a new annotated tag.

```bash
$ echo "more dummy" >> dummy.txt 

$ git add dummy.txt 

$ git commit -m "add a dummy line"

[master 420b390] add a dummy line
 1 file changed, 1 insertion(+)

$ git tag -a dummy3
```

3. We made a couple of commits. Can you add a tag to an arbitrary commit?

Yes.

```bash
$ git tag -a dummy2_2nd_tag 5d54e89

$ git log --oneline

420b390 (HEAD -> master, tag: dummy3) add a dummy line
5d54e89 (tag: dummy2_2nd_tag, tag: dummy2) adding more content to dummy.txt
7973d75 (tag: dummy) dummy commit
```

4. The exercise repository contains an annotated tag. What's the message?

```bash
$ git tag -n10

dummy           dummy commit
dummy2          don't worry, be happy
dummy2_2nd_tag  Second tag double time
dummy3          add one extra line to the dummy.txt file
```

5. Maybe not all of the tags are needed. Delete some of them.

```bash
$ git tag -d dummy

Deleted tag 'dummy' (was 7973d75)

$ git tag -d dummy2_2nd_tag

Deleted tag 'dummy2_2nd_tag' (was 011d52b)
```