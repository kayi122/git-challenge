# GIT ADVANCED EXERCISES
## Part 1:RFINING HISTORY FIT:
### 1.Missing File Fix:

```bash
# SOLUTION 
Run git status and git log to assess the current state of your repository.
From the status you will see that you forgot to add test4.md in the last commit.
Challenge: Recover from this error by staging/adding test4.md and amending the commit message with an appropriate description.

$ git add test4.md

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main|REBASE)
$  git log --oneline 
1db3d02 (HEAD) chore: Create third and fourth files
869ae4a chore: Create another file
e7eba3f chore: Create initial file
730c39e adding readme

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main|REBASE)
$ git commit --amend -m "chore: Create third and fourth files"
[detached HEAD 6b76dac] chore: Create third and fourth files
 Date: Thu Mar 6 13:03:37 2025 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
 create mode 100644 test4.md

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main|REBASE)
$  git log --oneline
6b76dac (HEAD) chore: Create third and fourth files
869ae4a chore: Create another file
e7eba3f chore: Create initial file
730c39e adding readme
 git status
On branch main
Your branch and 'origin/main' have diverged,
and have 2 and 2 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)


```
# Editing Commit History:
```bash
 # SOLUTION
 It's crucial to maintain accurate commit messages. Modify the message from "Create another file" to "Create second file".
Challenge: Utilize interactive rebasing (git rebase -i HEAD~2) to edit the commit message and ensure clarity. learn more about git rebase here

$ git rebase -i HEAD~2
[detached HEAD cc436dc] chore: Create a second  file
 Date: Thu Mar 6 12:36:49 2025 +0200
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md
Successfully rebased and updated refs/heads/main.

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git status
On branch main
Your branch and 'origin/main' have diverged,
and have 2 and 2 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

nothing to commit, working tree clean

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$  git log --oneline 
abdbf6d (HEAD -> main) Added test4.md
cc436dc chore: Create a second  file
e7eba3f chore: Create initial file
730c39e adding readme

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git rebase -i HEAD~2
error: cannot 'squash' without a previous commit
You can fix this with 'git rebase --edit-todo' and then run 'git rebase --continue'.
Or you can abort the rebase with 'git rebase --abort'.

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main|REBASE)
$ git rebase --abort

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git rebase -i HEAD~2
error: cannot 'squash' without a previous commit
You can fix this with 'git rebase --edit-todo' and then run 'git rebase --continue'.
Or you can abort the rebase with 'git rebase --abort'.



```
# 3.Keeping History Tidy - Squashing Commits:
``` bash
# SOLUTION
Squashing combines multiple commits into a single one. Let's merge "Create second file" into "Create initial file" for a cleaner history.
Challenge: Use interactive rebasing with the squash command to achieve this. learn more about squash here

$ git rebase -i HEAD~3
[detached HEAD 227d7cb] chore: Create initial and second file
 Date: Thu Mar 6 12:36:46 2025 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md
 create mode 100644 test2.md
Successfully rebased and updated refs/heads/main.

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$  git log --oneline
4f948da (HEAD -> main) Added test4.md
227d7cb chore: Create initial and second file
730c39e adding readme

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git status
On branch main
Your branch and 'origin/main' have diverged,
and have 2 and 3 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

nothing to commit, working tree clean
```
# 4.Splitting a Commit
```bash
# SOLUTION
Splitting a Commit:

Imagine "Create third and fourth files" describes too much at once. Separate them for better tracking with two different commit messages: "Create Third File" and "Create fourth file".
Challenge: Leverage git reset to separate the files into individual commits with distinct messages. learn more about splitting commits here

$ git add test3.md

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git commit -m"creating third file"
[main 7316230] creating third file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git add test4.md

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git commit -m"creating fourth file"
[main 89adbb0] creating fourth file
 create mode 100644 test3.md

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git add test4.md

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git commit -m"creating fourth file"
[main 89adbb0] creating fourth file

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git add test4.md

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git commit -m"creating fourth file"
[main 89adbb0] creating fourth file
USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git commit -m"creating fourth file"
[main 89adbb0] creating fourth file
$ git commit -m"creating fourth file"
[main 89adbb0] creating fourth file
[main 89adbb0] creating fourth file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test4.md

 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test4.md

 create mode 100644 test4.md

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git status
On branch main
Your branch and 'origin/main' have diverged,
and have 3 and 3 different commits each, respectively.
and have 3 and 3 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

nothing to commit, working tree clean

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$  git log --oneline
89adbb0 (HEAD -> main) creating fourth file
7316230 creating third file
227d7cb chore: Create initial and second file
730c39e adding readme

```
# 5.Advanced Squashing:
```bash
# SOLUTION
Let's explore more complex squashing. Can you combine the last two commits ("Create third file" and "Create fourth file") into a single commit named "Create third and fourth files"?
Challenge: Utilize interactive rebasing with the squash command to achieve this advanced squash

  git log --oneline
89adbb0 (HEAD -> main) creating fourth file
7316230 creating third file
227d7cb chore: Create initial and second file
730c39e adding readme

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git rebase -i HEAD~3
[detached HEAD f86c02e] creating third and fourth file
 Date: Thu Mar 6 14:08:40 2025 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
 create mode 100644 test4.md
Successfully rebased and updated refs/heads/main.

```
# 6.Dropping a Commit:
```bash
# SOLUTION 
We all make mistakes. Imagine needing to completely remove an unwanted commit from your history.

Create a new file named unwanted.txt add some changes and commit it with a message like "Unwanted commit".

Challenge: Use git rebase -i to identify and remove the "Unwanted commit" commit, cleaning up your history. learn more about dropping commits

 git add unwanted.txt
warning: in the working copy of 'unwanted.txt', LF will be replaced by CRLF the next time Git touches it

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git commit -m "Unwanted commit"
[main bf6940e] Unwanted commit
 1 file changed, 1 insertion(+)
 create mode 100644 unwanted.txt

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$  git log --oneline
bf6940e (HEAD -> main) Unwanted commit
f86c02e creating third and fourth file
227d7cb chore: Create initial and second file
730c39e adding readme

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git rebase -i HEAD~1
Successfully rebased and updated refs/heads/main.

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$  git log --oneline
f86c02e (HEAD -> main) creating third and fourth file
227d7cb chore: Create initial and second file
730c39e adding readme
```
# 7.Reordering Commits:
``` bash
# SOLUTION 
Delve deeper into git rebase -i. Can you rearrange commits within your history using this command? learn more about ordering commits 
SER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git rebase -i HEAD~2
Successfully rebased and updated refs/heads/main.

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$  git log --oneline
0770335 (HEAD -> main) chore: Create initial and second file
60114c9 creating third and fourth file
730c39e adding readme
```
# 8.Cherry-Picking Commits:
``` bash
# SOLUTION
Create a branch, call it ft/branch, and add a new file named test5.md with some content. Commit these changes with a message like "Implemented test 5".
Imagine you only desire a specific commit from ft/branch. Research and use git cherry-pick to selectively bring that commit into your current branch which is main.
learn more about cherry-pick
$ git checkout -b ft/branch
Switched to a new branch 'ft/branch'

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (ft/branch)
$ echo "This is test 5" > test5.md

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (ft/branch)
$ git add test5.md
warning: in the working copy of 'test5.md', LF will be replaced by CRLF the next time Git touches it

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (ft/branch)
$ git commit -m "Implemented test 5"
[ft/branch edd6d92] Implemented test 5
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git log ft/branch --oneline
edd6d92 (origin/ft/branch, ft/branch) Implemented test 5
0770335 (HEAD -> main) chore: Create initial and second file
60114c9 creating third and fourth file
730c39e adding readme
$ git log --oneline
fdf1699 (HEAD -> main) Implemented test 5
0770335 chore: Create initial and second file
60114c9 creating third and fourth file
730c39e adding readme

```

