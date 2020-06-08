# remove files from commit

I did a `git commit` but included a file I didn't want to commit. I haven't pushed the commit to a remote repository yet.
Use `git reset` to change the commit tree

    git reset --soft HEAD~1

We use the `--soft` option so the staging index and the working directory are left untouched.
Now look at which files are staged and unstaged with `git status`.
You can unstage the unneeded file with

    git reset HEAD <file>

and commit your changes again with the `--amend` option

    git commit --amend
