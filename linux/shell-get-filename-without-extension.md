# Get filename without the extension

`basename` will retrieve the last name from a pathname ignoring any trailing slashes

    $ basename /home/jsmith/base.wiki
    base.wiki

    $ basename /home/jsmith/
    jsmith

    $ basename /
    /

`basename` takes a second parameter that can be used to remove an extension if known

    $ basename /home/jsmith/base.wiki .wiki
    base

    $ basename /home/jsmith/base.wiki ki
    base.wi

[source](https://en.wikipedia.org/wiki/Basename)
