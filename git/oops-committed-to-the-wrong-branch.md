# Oops, I accidentally committed to the wrong branch!

Undo the last commit, but leave the changes available

    git reset HEAD~ --soft

When you run `git reset HEAD~ --soft` HEAD now points to the parent of HEAD, but the index still has the previous changes; git status will show them as staged.

Now you can stash your changes...

    git stash

move to the correct branch
  
 git checkout name-of-the-correct-branch
git stash pop

now add your files again to the stage
and then commit

    git commit -m "your message here"

This time your changes are on the correct branch.

## Background

The option `--hard` also modifies your working directory. So you would permanently lose your changes.

When you would run `git reset HEAD~` you would use the default option `--mixed`.

HEAD would point to the parent of HEAD, and the index would also match the parent of HEAD. Doing a `git status` will show them as unstaged.

Source: https://stackoverflow.com/a/3528483/6570344
