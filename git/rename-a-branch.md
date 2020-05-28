# How do I rename a local branch?

To rename a branch while pointed to any branch, do:

    git branch -m <oldname> <newname>

If you want to rename the current branch, you can do:

    git branch -m <newname>

Afterwards update your local branch's tracking reference to the new remote:

    git push origin --delete old_branch

Push the new branch, set local branch to track the new remote

    git push --set-upstream origin new_branch
