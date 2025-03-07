# GIT ADVANCED EXERCISES
## Part 1:REFINING HISTORY FIT:
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
#  PART 2.BRANCHING BASICS
## 1.Feature Branch Creation:
``` bash
# SOLUTION
Imagine working on a new feature named ft/new-feature. Let's establish a dedicated branch for it.
Challenge: Create a new branch named ft/new-feature and switch to that branch.

git branch ft/new-feature

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git checkout ft/new-feature
M       README.md
Switched to branch 'ft/new-feature'

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (ft/new-feature)
$ git branch
  ft/branch
* ft/new-feature
```
# 2. Working on the Feature Branch:
```bash
# SOLUTION
Create a new file named feature.txt in this branch and add some content to it.
Commit these changes with a descriptive message like "Implemented core functionality for new feature".
 
 /branch
* ft/new-feature
  main

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (ft/new-feature)
$ echo "This is the core functionality for the new feature." > feature.txt

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (ft/new-feature)
$ git add feature.txt
warning: in the working copy of 'feature.txt', LF will be replaced by CRLF the next time Git touches it

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (ft/new-feature)
$ git commit -m "Implemented core functionality for new feature"
[ft/new-feature 59c84bd] Implemented core functionality for new feature
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt
```
# 3.Switching Back and Making More Changes:
``` bash
# SOLUTION
It's common to switch between branches during development.
Challenge: Switch back to the main branch (previously master) and create a new file named readme.txt with some introductory content. Commit these changes with a message like "Updated project readme".

 git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ echo "This is the project readme file." > readme.txt

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git add readme.txt
warning: in the working copy of 'readme.txt', LF will be replaced by CRLF the next time Git touches it

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git commit -m "Updated project readme"
[main 88bd461] Updated project readme
 1 file changed, 1 insertion(+)
 create mode 100644 readme.txt

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git log --oneline
88bd461 (HEAD -> main) Updated project readme
38689ff (origin/main) adding final readme
c025119 Merge branch 'main' of https://github.com/kayi122/git-challenge
fc51a15 adding README.md
fdf1699 Implemented test 5
0770335 chore: Create initial and second file
60114c9 creating third and fourth file
e476f89 Added test4.md
3c2f9b9 chore: Create another file
e7eba3f chore: Create initial file
730c39e adding readme

```
# 4.Local vs. Remote Branches:
``` bash
# SOLUTION
So far, we've been working with local branches that exist on your machine. Research the concept of remote branches, which are copies of your local branches stored on a Git hosting platform like GitHub. Learn how to push your local branches to remote repositories and pull changes from them to keep your local and remote repositories in sync.

$ git branch -r
  origin/ft/branch
  origin/ft/new-feature
  origin/main

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (ft/new-feature)
$ git fetch origin

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (ft/new-feature)
$ git branch -r
  origin/ft/branch
  origin/ft/new-feature
  origin/main

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (ft/new-feature)
$ git pull origin main
From https://github.com/kayi122/git-challenge
 * branch            main       -> FETCH_HEAD
Already up to date.

```
# 5.Branch Deletion:
``` bash
# SOLUTION
After merging or completing work on a feature branch, it's good practice to remove it.
Challenge: Delete the ft/new-feature branch once you're confident the changes are integrated into main
git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git branch -d ft/new-feature
warning: deleting branch 'ft/new-feature' that has been merged to
         'refs/remotes/origin/ft/new-feature', but not yet merged to HEAD
Deleted branch ft/new-feature (was 59c84bd).

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git push origin --delete ft/new-feature
To https://github.com/kayi122/git-challenge.git
 - [deleted]         ft/new-feature

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git branch -r
  origin/ft/branch
  origin/main
  ```
  # 6.Creating a Branch from a Commit:
``` bash
# SOLUTION
$ git checkout -b ft/new-branch-from-commit 88bd461
Switched to a new branch 'ft/new-branch-from-commit'

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (ft/new-branch-from-commit)
$ git branch
  ft/branch
* ft/new-branch-from-commit
  main

```
# 7.Branch Merging:
``` bash
# SOLUTION
 git merge ft/new-branch-from-commit
Already up to date.

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (ft/new-branch-from-commit)
$ git branch
  ft/branch
* ft/new-branch-from-commit
  main
```
# 8.Branch Rebasing:
```bash
# SOLUTION
USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (ft/new-branch-from-commit)
$ git checkout ft/new-branch-from-commit
Already on 'ft/new-branch-from-commit'

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (ft/new-branch-from-commit)
$ git rebase main
Current branch ft/new-branch-from-commit is up to date.

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (ft/new-branch-from-commit)
$ git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git merge ft/new-branch-from-commit --ff-only
Already up to date.

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git branch -d ft/new-branch-from-commit
Deleted branch ft/new-branch-from-commit (was 88bd461).

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (main)
$ git branch -r
  origin/ft/branch
  origin/main
```
# 9.Renaming Branches:
```bash
# SOLUTION
$ git branch -m ft/improved-branch-name

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (ft/improved-branch-name)
$ git branch
  ft/branch
* ft/improved-branch-name

```
# 10.Checking Out Detached HEAD:
```bash
# SOKUTION
  git checkout 38689ff
Note: switching to '38689ff'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 38689ff adding final readme

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge ((38689ff...))
$ git status
HEAD detached at 38689ff
nothing to commit, working tree clean

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge ((38689ff...))
$ git checkout -b new-branch-name
Switched to a new branch 'new-branch-name'

USER@DESKTOP-0LNSN88 MINGW32 ~/Desktop/git-challenge (new-branch-name)
$ git checkout main
branch 'main' set up to track 'origin/main'.
Switched to a new branch 'main'

```



