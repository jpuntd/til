# List of files that have been removed from a git repository

If you want a list of all the files that were removed, you can use

    git log --diff-filter=D --summary | grep delete

If you want a list of all the files that were added, you can use

    git log --diff-filter=A --summary | grep create
