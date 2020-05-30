# read and adapt git config

Git stores configuration in the following files:

- a _system_ wide `/etc/gitconfig` file
- a _global_ configuration specific for each user
- a _local_ configuration inside a git repository

Every level overwrites values in the previous level.

To list what is inside a config:

    git config --local --list

To open an editor and change the configuration:

    git config --global --edit

To read a specific config:

    git config --local user.email

To set a specific config:

    git config --global core.editor code
