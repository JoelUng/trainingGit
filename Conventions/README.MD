# Some conventions when working with Git
---

## Avoiding merge commits

When you want to update your local branch by typing :
```
  git pull
```
Git will make a merge to merge your changes and those you just retrieved.
--

On the remote branch :
```
 A---B---C---D---E
```
--

On your local branch :
```
          origin/master
         /
A---B---C---F ← master
```
--

After pulling :
```
          D---E ← origin/master
         /     \
A---B---C---F---G ← master
```
G is a merge commit and Git has created a branch to merge your work. This branch is unnecessary because it does not make any sense.
--

To avoid this, you can use the --rebase option :
```
  git pull --rebase
```
It will produce this result :
```
                  origin/master
                 /
A---B---C---D---E---F ← master
```