# How to rebase

This practise will train you to rebase Git branches

## How to rebase a local branch with a remote one

Here is the current state :
```
  O---A---B---C <- common branch named feat-common-branch
   \--D---E <- local branch named feat-rebase
```

From the common branch, a new branch named feat-rebase have been created from the commit O with the commits D and E.
On the common branch, the commits A, B and C have been made.

We want the branch feat-rebase to be merged inline on the common branch.
```
O---A---B---C---D---E
```

Checkout the branch named "feat-rebase" :
```
  git fetch
  git checkout -b feat-rebase origin/feat-rebase
```

Rebase the local branch with the common branch :
```
  git pull --rebase origin feat-common-branch
```

This command is equivalent to :
```
  git fetch origin            # Updates origin/master
  git rebase origin/master    # Rebases current branch onto origin/master
```

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
