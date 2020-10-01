# Play sound as a notification

You have a long running process and want to be notified when the command has exited.
Echo a bell character as the last command.

    rm -rf ./node_modules && echo ^G

The `^G` character stands for <kbd>Ctrl</kbd> + <kbd>G</kbd>. When directly typed, it will sound a bell.

Type <kbd>Ctrl</kbd> + <kbd>V</kbd> and then <kbd>Ctrl</kbd> + <kbd>G</kbd> to produce it in a command.

## Alternatives

    echo -e "\a"
    printf '\a'
    echo -e "\007"
