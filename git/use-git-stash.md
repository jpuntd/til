# Use git stash

You need to temporarily work on something else and don't want to commit.

    $ git status
    On branch master
    Changes to be committed:
    new file: style.css
    Changes not staged for commit:
    modified: index.html
    Untracked files:
    script.js

Do

    git stash -u save "optional message for yourself"

This will save your uncommitted changes (both staged and unstaged) and then reverts them from your working copy. The `-u` option also stashed the untracked file:

    $ git status
    On branch master
    nothing to commit, working tree clean

## Look at your stashes

    git stash list

returns a list of your saved snapshots in the format

If you forgot what changes were made in the stash, you can see a summary of them.

    git stash show stash@{2}

**stash@{0}: BRANCH-STASHED-CHANGES-ARE-FOR: MESSAGE**

## Reuse stashed changes

    $ git stash pop
    On branch master
    Changes to be committed:
    new file: style.css
    Changes not staged for commit:
    modified: index.html
    Dropped refs/stash@{0} (32b3aa1d185dfe6d57b3c3cc3b32cbf3e380cc6a)

If you don't want to lose the stash (see last line), use

    git stash apply

By default, git stash pop will re-apply the most recently created stash: `stash@{0}`

Otherwise use

    git stash pop stash@{2}

## Create a new branch

Check out a new branch based on the commit that you created your stash from, and then pops your stashed changes onto it.

    git stash branch add-stylesheet stash@{1}

[source](https://www.atlassian.com/git/tutorials/saving-changes/git-stash)
