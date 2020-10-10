# Manage credentials

Why git config has a `credential.helper=...` line?

It's possible to have a key without a passphrase when using ssh.
Connecting to remotes through http requires a username and a password.
When connecting, Git invokes a separate program with name `git-credential-...`

On Windows git config has a `credential.helper=manager` line.
So on Windows the git-credential-manager is invoked.
