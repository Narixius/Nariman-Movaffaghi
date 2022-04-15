# Question 1

1.
```bash
> git init
Initialized empty Git repository in /Semester 8/WEB/assignment#1/.git/
```
2.
```bash
> git add ./file.txt
> git commit -m "first commit"
[master (root-commit) c743e22] first commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 file.txt
 ```
3.
```bash
> tree ./.git

./.git
├── COMMIT_EDITMSG
├── FETCH_HEAD
├── HEAD
├── config
├── description
├── hooks
│   ├── applypatch-msg.sample
│   ├── commit-msg.sample
│   ├── fsmonitor-watchman.sample
│   ├── post-update.sample
│   ├── pre-applypatch.sample
│   ├── pre-commit.sample
│   ├── pre-merge-commit.sample
│   ├── pre-push.sample
│   ├── pre-rebase.sample
│   ├── pre-receive.sample
│   ├── prepare-commit-msg.sample
│   ├── push-to-checkout.sample
│   └── update.sample
├── index
├── info
│   └── exclude
├── logs
│   ├── HEAD
│   └── refs
│       └── heads
│           └── master
├── objects
│   ├── 80
│   │   └── 2992c4220de19a90767f3000a79a31b98d0df7
│   ├── 9e
│   │   └── 18d0c29660a94f06d71124b2771ac6046b04fd
│   ├── f4
│   │   └── 97ea8188174179405fae6712aeb53800ca6cb2
│   ├── info
│   └── pack
└── refs
    ├── heads
    │   └── master
    └── tags

14 directories, 26 files
```


4.
```bash
> find ./.git/objects -type f

./.git/objects/bd/d68b0120ca91384c1606468b4ca81b8f67c728
./.git/objects/c7/43e2283e4a951b645b637b5ea104119a29904a
./.git/objects/e6/9de29bb2d1d6434b8b29ae775ad8c2e48c5391
```

```bash
> git cat-file -t 802992c4220de19a90767f3000a79a31b98d0df7
blob
> git cat-file -p 802992c4220de19a90767f3000a79a31b98d0df7
Hello world

> git cat-file -t 9e18d0c29660a94f06d71124b2771ac6046b04fd
tree
> git cat-file -p 9e18d0c29660a94f06d71124b2771ac6046b04fd
100644 blob 802992c4220de19a90767f3000a79a31b98d0df7    file.txt

> git cat-file -t f497ea8188174179405fae6712aeb53800ca6cb2
commit
> git cat-file -p f497ea8188174179405fae6712aeb53800ca6cb2
tree 9e18d0c29660a94f06d71124b2771ac6046b04fd
author Nariman Movaffaghi <nariman.movaffaghi@gmail.com> 1649959729 +0430
committer Nariman Movaffaghi <nariman.movaffaghi@gmail.com> 1649959729 +0430

first commit
```
در این بخش مشخص میشود که در وضعیت فعلی گیت، ۳ آبجکت وجود دارد که هر کدون یک تایپ دارند. یکی `tree` بوده، یکی `commit` و دیگری `blob`. محتوای هر کدام نمایش داده شده است.

5.
```bash
> cat ./.git/HEAD
ref: refs/heads/master

> cat ./.git/refs/heads/master
f497ea8188174179405fae6712aeb53800ca6cb2
```
در اینحا مشخص میشود که HEAD ما همان کامیتی است که ایجاد شده.


# Question 2


```bash
> git clone https://github.com/idin-khayami/git-exercises
Cloning into 'git-exercises'...
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 9 (delta 1), reused 8 (delta 0), pack-reused 0
Receiving objects: 100% (9/9), done.
Resolving deltas: 100% (1/1), done.

> cd git-exercises
> git checkout question2
Branch 'question2' set up to track remote branch 'question2' from 'origin'.
Switched to a new branch 'question2'
```

1.
```bash
> git ls-files -s
100644 980a0d5f19a64b4b30a87d4206aade58726b60e3 0       hello.txt
```

2.
```bash
> git add -p
diff --git a/hello.txt b/hello.txt
index 980a0d5..0e7763f 100644
--- a/hello.txt
+++ b/hello.txt
@@ -1 +1,3 @@
 Hello World!
+
+changeee
(1/1) Stage this hunk [y,n,q,a,d,e,?]? y
```

3.
```bash
> git reset HEAD --hard
```

4.
```bash
> git stash -m "my changes"
Saved working directory and index state On question2: my changes

> git stash apply "stash@{0}"
On branch question2
Your branch is up to date with 'origin/question2'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   hello.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
در این قسمت برای اپلای کردن همان استشی که ایجاد کردیم، اول `git stash list` زدم تا لیست استش ها را ببینم و آیدی استشی که با نام `my changes` ایجاد شده بود را برای برگرداندن تغییرات استش شده استفاده کردم.


# Question 3
```bash
> cat ./.git/HEAD
ref: refs/heads/question3

> cat ./.git/refs/heads/question3
19f9daed9feb5c5e5ee8149f9677505af7bec379

> git cat-file -t 19f9daed9feb5c5e5ee8149f9677505af7bec379
commit

> git cat-file -p 19f9daed9feb5c5e5ee8149f9677505af7bec379
tree cbcdf5dda7853d595fe0b1942cb0d1d72eb910f3
parent 84f33bb71faa62192b2362ad0ef66fb7d972e447
author Idin Khayami <idin.khanoom.khayami@gmail.com> 1649332870 +0430
committer Idin Khayami <idin.khanoom.khayami@gmail.com> 1649332870 +0430

add update for question 3
```
در اینجا کامیتی که `HEAD` است، کامیتی است که برای برنچ `question3` ساخته شده است.

2.
```bash
> git show-ref
84f33bb71faa62192b2362ad0ef66fb7d972e447 refs/heads/master
84f33bb71faa62192b2362ad0ef66fb7d972e447 refs/heads/question2
19f9daed9feb5c5e5ee8149f9677505af7bec379 refs/heads/question3
84f33bb71faa62192b2362ad0ef66fb7d972e447 refs/remotes/origin/HEAD
84f33bb71faa62192b2362ad0ef66fb7d972e447 refs/remotes/origin/master
84f33bb71faa62192b2362ad0ef66fb7d972e447 refs/remotes/origin/question2
19f9daed9feb5c5e5ee8149f9677505af7bec379 refs/remotes/origin/question3
84f33bb71faa62192b2362ad0ef66fb7d972e447 refs/remotes/origin/question4
87cba9c704760c7922a5a07ad3cbe7d6ccbd245e refs/remotes/origin/question5
ecf775755e7373ddad4bb29cca02a0bd881e3db9 refs/stash
```

3.
```bash
> git tag lightweight
> git tag -l --points-at 19f9daed9feb5c5e5ee8149f9677505af7bec379
lightweight
```
در این بخش برای اینکه ببینیم چه تگی برای کامیتی که `‍HEAD` این برنچ است تنظیم شده است، از دستور `git tag` استفاده میکنیم و هَشِ `HEAD` را فیلتر میکنیم که مشخص میشود که تگ `lightweight` به ‍‍`HEAD` اشاره میکند.

4.
```bash
> git tag -a annotated-tag -m "this tag is annotated"
no res

> git tag
annotated-tag
lightweight

> git show annotated-tag

tag annotated-tag
Tagger: Nariman Movaffaghi <nariman.movaffaghi@gmail.com>
Date:   Thu Apr 14 23:35:58 2022 +0430

this tag is annotated

commit 19f9daed9feb5c5e5ee8149f9677505af7bec379 (HEAD -> question3, tag: lightweight, tag: annotated-tag, origin/question3)
Author: Idin Khayami <idin.khanoom.khayami@gmail.com>
Date:   Thu Apr 7 16:31:10 2022 +0430

    add update for question 3

diff --git a/hello.txt b/hello.txt
index 980a0d5..b31a35b 100644
--- a/hello.txt
+++ b/hello.txt
@@ -1 +1,2 @@
 Hello World!
+This is a test of the emergency git-casting system.

```

5.
```bash
> git checkout 84f33bb71faa62192b2362ad0ef66fb7d972e447
Note: switching to '84f33bb71faa62192b2362ad0ef66fb7d972e447'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 84f33bb initial commit
```

```bash
> cat ./.git/HEAD
84f33bb71faa62192b2362ad0ef66fb7d972e447
```
زمانی که `HEAD` را چک میکنیم مشخص است که به کامیتی که ما ست کردیم اشاره دارد.

6.
```bash
> git add hello.txt
> git commit -m "changes on the branch question3"
[detached HEAD e9242c6] changes on the branch question3
 1 file changed, 2 insertions(+)
> git checkout question4
Warning: you are leaving 1 commit behind, not connected to
any of your branches:

  e9242c6 changes on the branch question3

If you want to keep it by creating a new branch, this may be a good time
to do so with:

 git branch <new-branch-name> e9242c6

Switched to branch 'question4'
Your branch is up to date with 'origin/question4'.
```


# Question 4

1.
```bash
> git merge question3
Updating 84f33bb..19f9dae
Fast-forward
 hello.txt | 1 +
 1 file changed, 1 insertion(+)

> git log
commit 19f9daed9feb5c5e5ee8149f9677505af7bec379 (HEAD -> question4, tag: lightweight, tag: annotated-tag, origin/question3, question3)
Author: Idin Khayami <idin.khanoom.khayami@gmail.com>
Date:   Thu Apr 7 16:31:10 2022 +0430

    add update for question 3

commit 84f33bb71faa62192b2362ad0ef66fb7d972e447 (origin/question4, origin/question2, origin/master, origin/HEAD, question2, master)
Author: Idin Khayami <idin.khanoom.khayami@gmail.com>
Date:   Thu Apr 7 16:26:47 2022 +0430

    initial commit
```
در گیت لاگ، کامیتی از برنچ `question3` اضافه شده که نشان میدهد `merge` درست انجام شده است.

2.
```bash
> git reset --hard HEAD^
HEAD is now at 84f33bb initial commit


> git merge question3 --no-ff
Merge made by the 'recursive' strategy.
 hello.txt | 1 +
 1 file changed, 1 insertion(+)

> git log
commit 98c9d1130ef097638311cce62f617321b18f4183 (HEAD -> question4)
Merge: 84f33bb 19f9dae
Author: Nariman Movaffaghi <nariman.movaffaghi@gmail.com>
Date:   Fri Apr 15 00:01:32 2022 +0430

    Merge branch 'question3' into question4

commit 19f9daed9feb5c5e5ee8149f9677505af7bec379 (tag: lightweight, tag: annotated-tag, origin/question3, question3)
Author: Idin Khayami <idin.khanoom.khayami@gmail.com>
Date:   Thu Apr 7 16:31:10 2022 +0430

    add update for question 3

commit 84f33bb71faa62192b2362ad0ef66fb7d972e447 (origin/question4, origin/question2, origin/master, origin/HEAD, question2, master)
Author: Idin Khayami <idin.khanoom.khayami@gmail.com>
Date:   Thu Apr 7 16:26:47 2022 +0430

    initial commit
```
در این بخش علاوه بر کامیت هایی که از برنچ `question3` آمده، یک کامیت دیگر هم ثبت شده که نشان میدهد که در اینجا برنچ `question4` با `question3`، مِرج شده است.

3.
```bash
> git checkout question5
Branch 'question5' set up to track remote branch 'question5' from 'origin'.
Switched to a new branch 'question5'
> git add hello.txt
> git commit -m "new changes on question5"
[question5 b94fbfe] new changes on question5
 1 file changed, 3 insertions(+), 1 deletion(-)
> git merge question4
Auto-merging hello.txt
CONFLICT (content): Merge conflict in hello.txt
Automatic merge failed; fix conflicts and then commit the result.
```
در اینجا تغییراتی در برنچ `question5` انجام شد و بعد از آن برای مرج کردن با برنچ `question4` به کانفلیکت برخوردیم.

4.
```bash
> git config rerere.enabled true
> git rerere
> git add hello.txt
> git commit -m "merge fixes"
```
کانفلیکت را حل کردیم و مرج کردیم و مرج شد.

5.

```bash
> git reset HEAD^ --hard
HEAD is now at 87cba9c add update for question 5
> git add hello.txt
> git commit -m "new changes on question5"
[question5 c52fe3e] new changes on question5
 1 file changed, 3 insertions(+), 1 deletion(-)
> git merge question4
Auto-merging hello.txt
CONFLICT (content): Merge conflict in hello.txt
Resolved 'hello.txt' using previous resolution.
Automatic merge failed; fix conflicts and then commit the result.

the result is how I fixed it before
```
در اینجا مشابه حالتی که ما قبلا کانفلیکت را فیکس کردیم، کانفلیکت را فیکس کرد بدون اینکه حالت فایل را به حالت کانفلیکت نیاز به بررسی در بیاورد.


# Question 5

1.
```bash
> git add hello.txt
> git commit -m "new changes on question5"
[question5 87b2641] new changes on question5
 1 file changed, 3 insertions(+), 1 deletion(-)
```
2.
```bash
> git add hello_changename.txt
> git commit -m "change file name"
[question5 b342342] change file name
 1 file changed, 4 insertions(+)
 create mode 100644 hello_changename.txt
```
کامیت هایی که به تغییر نام این فایل اشاره میکنند:
```bash
> git log --name-status --follow hello_changename.txt

commit b3423427ef9e618be1e4f5d12236de138f8bd8dc (HEAD -> question5)
Author: Nariman Movaffaghi <nariman.movaffaghi@gmail.com>
Date:   Fri Apr 15 01:15:16 2022 +0430

    change file name

C100    hello.txt       hello_changename.txt

commit 87b26419ea6eeca0274b9c6879cef6c9cb5dec72
Author: Nariman Movaffaghi <nariman.movaffaghi@gmail.com>
Date:   Fri Apr 15 01:12:36 2022 +0430

    new changes on question5

M       hello.txt

commit 87cba9c704760c7922a5a07ad3cbe7d6ccbd245e (origin/question5)
Author: Idin Khayami <idin.khanoom.khayami@gmail.com>
Date:   Thu Apr 7 16:35:47 2022 +0430

    add update for question 5

M       hello.txt

commit 84f33bb71faa62192b2362ad0ef66fb7d972e447 (origin/question4, origin/question2, origin/master, origin/HEAD, question2, master)
Author: Idin Khayami <idin.khanoom.khayami@gmail.com>
Date:   Thu Apr 7 16:26:47 2022 +0430

    initial commit
```
کامیت هایی که در آن ها کلمه `questi‍on` استفاده شده است.
```bash
> git log --grep "question"
commit 87b26419ea6eeca0274b9c6879cef6c9cb5dec72
Author: Nariman Movaffaghi <nariman.movaffaghi@gmail.com>
Date:   Fri Apr 15 01:12:36 2022 +0430

    new changes on question5

commit 87cba9c704760c7922a5a07ad3cbe7d6ccbd245e (origin/question5)
Author: Idin Khayami <idin.khanoom.khayami@gmail.com>
Date:   Thu Apr 7 16:35:47 2022 +0430

    add update for question 5
```
کامیت هایی که در آن ها تغییر(Modification - M) و تغییر نام(Rename - R) صورت گرفته:
```bash
> git log  --diff-filter=RM
commit 87b26419ea6eeca0274b9c6879cef6c9cb5dec72
Author: Nariman Movaffaghi <nariman.movaffaghi@gmail.com>
Date:   Fri Apr 15 01:12:36 2022 +0430

    new changes on question5

commit 87cba9c704760c7922a5a07ad3cbe7d6ccbd245e (origin/question5)
Author: Idin Khayami <idin.khanoom.khayami@gmail.com>
Date:   Thu Apr 7 16:35:47 2022 +0430

    add update for question 5
```
3.
```bash
> git show 87b26419ea6eeca0274b9c6879cef6c9cb5dec72

commit 87b26419ea6eeca0274b9c6879cef6c9cb5dec72
Author: Nariman Movaffaghi <nariman.movaffaghi@gmail.com>
Date:   Fri Apr 15 01:12:36 2022 +0430

    new changes on question5

diff --git a/hello.txt b/hello.txt
index 47ad6c9..4f07bd9 100644
--- a/hello.txt
+++ b/hello.txt
@@ -1,2 +1,4 @@
 Hola Mundo!
-This is a test of the emergency git-casting system.
\ No newline at end of file
+This is a test of the emergency git-casting system.
+
+new changes on question 5
```
```bash
> git branch --merged
master
question2
question5

> git branch --no-merged
question3
question4
```
