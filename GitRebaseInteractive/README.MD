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
* 9d7ab16 - fix: add eol for titi (Joel Ung 11 minutes ago)
* 18d9cbf - test: test for titi (Joel Ung 12 minutes ago)
* f14b48e - feat: add titi (Joel Ung 12 minutes ago)
* a624ed7 - test: add tests for toto (Joel Ung 44 minutes ago)
* a5cb461 - feat: add toto (Joel Ung 45 minutes ago)
```
--

We want to fix the git history before pushing it to the remote repository.
* First, in case of TDD design, we should have written the tests before writing the code. So we move the test commits as the oldest commits.
* Second, we have some useless commits we want to get rid of. We will fix them.

--

Let's checkout the git branch :
```git
  git checkout -b feat-rebase-interactive
```

And then let's do the rebase together.
