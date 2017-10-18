# How to rebase

This practise will train you to rebase Git branches
---

## How to rebase a local branch with a remote one

Here is the current state :
```
  O---A---B---C <- common branch named feat-common-branch
   \--D---E <- local branch named feat-rebase
```
--

From the common branch, a new branch named feat-rebase have been created from the commit O with the commits D and E.
On the common branch, the commits A, B and C have been made.

We want the branch feat-rebase to be merged inline on the common branch.
```
O---A---B---C---D---E
```
--

Checkout the branch named "feat-rebase" :
```
  git fetch
  git checkout -b feat-rebase origin/feat-rebase
```
--

Rebase the local branch with the common branch :
```
  git pull --rebase origin feat-common-branch
```

This command is equivalent to :
```
  git fetch origin            # Updates origin/master
  git rebase origin/master    # Rebases current branch onto origin/master
```
--

Display the local Git history :
```
  git log --oneline
```
It should display an inline history as :
```
fb01100 feat: E
3ea6e2a feat: D
0dee120 feat: C
7cd857f feat: B
d1bf978 feat: A
1c4c7c7 feat: O
[...]
```
---

## How to rebase a local branch with a remote one with conflict

Here is the current state :
```
  O---A---B---C <- common branch named feat-common-branch
   \--quoted A <- local branch named feat-rebase-conflict
```
--

From the common branch, a new branch named feat-rebase-conflict have been created from the commit O with the commit .
On the common branch, the commits A, B and C have been made.

We want the branch feat-rebase to be merged inline on the common branch.
```
O---A---B---C---quoted A
```
--

Checkout the branch named "feat-rebase" :
```
  git fetch
  git checkout -b feat-rebase-conflict origin/feat-rebase-conflict
```
--

Rebase the local branch with the common branch :
```
  git pull --rebase origin feat-common-branch
```
--

It will displayed a CONFLICT to handle :
```
λ git pull --rebase origin feat-common-branch
From https://github.com/JoelUng/trainingGit
 * branch            feat-common-branch -> FETCH_HEAD
First, rewinding head to replay your work on top of it...
Applying: feat: quoted A
Using index info to reconstruct a base tree...
Falling back to patching base and 3-way merge...
Auto-merging GitRebase/A.txt
CONFLICT (add/add): Merge conflict in GitRebase/A.txt
error: Failed to merge in the changes.
Patch failed at 0001 feat: quoted A
The copy of the patch that failed is found in: .git/rebase-apply/patch

When you have resolved this problem, run "git rebase --continue".
If you prefer to skip this patch, run "git rebase --skip" instead.
To check out the original branch and stop rebasing, run "git rebase --abort".
```
--

This conflict is because both branches contain modifications on the same file A.txt and on the same line :
```
A
```
and
```
'A'
```
So Git does not know which modification it should keep.
As for this example, we want to keep the modification with the quoted A : 'A'.
So we will edit the file in order to have this result :
```
'A'
```
--

Then, we want Git to keep this change :
```
  git add GitRebase/A.txt
```
And finally, we want Git to continue the rebase :
```
  git rebase --continue
```
--

Now the branch is rebased with feat-common-branch and the history should be :
```
e665a5a feat: quoted A
0dee120 feat: C
7cd857f feat: B
d1bf978 feat: A
1c4c7c7 feat: O
[...]
