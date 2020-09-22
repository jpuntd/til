# show complete git configuration

Git stores configuration in the following files:

- a _system_ wide `/etc/gitconfig` file
- a _global_ configuration specific for each user
- a _local_ configuration inside a git repository `.git/config`

Every level overwrites values in the previous level.

Show configuration valid in a certain repo + where it is defined.

    git config --list --show-origin

To open an editor and change the configuration:

    git config --global --edit

To set a specific config:

    git config --global core.editor code
