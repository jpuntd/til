# Pass a parameter to an existing parameter script

The syntax is as follows:

    npm run <command> [-- <args>]

Note the necessary --. It is needed to separate the params passed to npm command itself and params passed to your script.

## Example

    npm run test -- --watch
