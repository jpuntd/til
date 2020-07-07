# show a stacktrace for warnings displayed when running tests

Node started displaying warnings for unhandled Promise rejections. Jest would run and in between tests messages would be displayed like

    UnhandledPromiseRejectionWarning: TypeError: Cannot read property 'id' of undefined

No stack trace or even filename is being diplayed. How to get more information?

## Pass arguments to Node while starting Jest

An argument like `--trace-warnings` or `--unhandled-rejections=strict` will make Node show a complete error message when encountering an unhandled rejection.

    node --trace-warnings ./node_modules/.bin/jest [any other arguments here]

or on Windows

    node --trace-warnings ./node_modules/jest/bin/jest.js  [any other arguments here]

[source](https://jestjs.io/docs/en/troubleshooting)

## Add an unhandledRejection event handler to Jest setup file

Jest has a configuration for setupFiles. Inside the setup file include something like...

    process.on('unhandledRejection', (reason) => {
        console.warn('REJECTION', reason)
    })

All warnings will be accompanied by a stack trace.

[source](https://github.com/facebook/jest/issues/3251)
