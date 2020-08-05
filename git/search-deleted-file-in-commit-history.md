# Search file in commit history that has since been deleted

Want to find a file that was once part of the repo, but had since been deleted and added to `.gitignore`

    git log --all --full-history -- "**/.npmrc"
