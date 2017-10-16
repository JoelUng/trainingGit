# Interactive rebase

Git allows the history to be completely rewritten. One tool for this purpose is rebase.
"you can use the rebase tool to rebase a series of commits onto the HEAD they were originally based on instead of moving them to another one." [Git documentation link](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History)

# How to rebase interactively
If you need to make some changes to the 3 last commits, or any commit among them, you have to run :

```git
  git rebase -i HEAD~3
```

Note : to rebase do not move your commits but create new commits with new id with the same content. That's because the commit id is based on the content's HASH.

# Practice

Here is the situation :
```
TODO
```

Let's checkout the git branch :
```git
  git checkout -b feat-rebase-interactive
```
