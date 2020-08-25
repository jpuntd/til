# Push subtree of a repository to a separate branch

On the master branch we have a subdirectory `build`.
We want to publish this directory as a _Github Pages_ webpage.
That's why we want this subdirectory to be the root directory of a `gh-pages` branch.

    git subtree push --prefix build origin gh-pages

Use the prefix flag to set the local directory into which you want to pull the subtree.

If you make a change to anything in `build` the commit will be stored in the **host repository**.

If you now want to update the subtree remote repository with that commit, you must run the same command again.

[source](https://gist.github.com/cobyism/4730490)
