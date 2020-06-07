# npm link in one step

`npm link` allows to point directly to source code of a library or package that is available on your pc. Linking happens in 2 steps:

1. Run `npm link` from the root folder of the library you consume. It will make that library linkable from another project.

2. Run `npm link <name-of-linked-library>` to consume the linked library from another project.

Today I learned there is a shortcut where you do the two steps in one. In our project we do

    npm link ../node_modules/react

which is the same as …

    (from inside the directory of project)
    cd ../node_modules/react
    npm link
    (go back to the directory of project)
    npm link react
