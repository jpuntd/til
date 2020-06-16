# check that ssh-agent is running

Run the following command to grep `ssh-agent` from the list of running processes.

    ps ax | grep ssh-agent

It should show a line like the following

    1485       1    1485      18696  ?        1065218   Jun 10  /usr/bin/ssh-agent

The question mark is there because running as a daemon, `ssh-agent` isn't tied to a terminal.

## if ssh-agent is not running, start it with

    eval $(ssh-agent -s)

and add default key with

    ssh-add

## test your ssh connection

    ssh -T git@hostname
