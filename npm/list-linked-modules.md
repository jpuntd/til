# List all linked modules

    npm ls -g --depth=0 --link=true

The `-g` global flag is necessary because when you use npm link, the linked module is installed globally. See [npm documentation](https://docs.npmjs.com/cli/link#:~:text=npm%20link%20in%20a%20package%20folder%20will%20create%20a%20symlink%20in%20the%20global%20folder).

The command returns something like ...

    +-- ui@1.4.0-beta.8 -> C:\Users\jpuntd\dev\ui
    +-- utils@1.5.0-beta.27 -> C:\Users\jpuntd\dev\utils
    `-- react@16.13.1 -> C:\Users\jpuntd\dev\benchmark\node_modules\react

To remove or unlink a package...

    npm unlink utils -g
