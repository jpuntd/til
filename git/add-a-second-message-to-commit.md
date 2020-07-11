# add multiple lines to a commit message by using `-m` twice

Today I learned you can add multiple lines in a commit message by using `-m` twice:

    git commit -m "add css" -m "transform starts new stacking context"

The values are concatenated as paragraphs. So you'll still have a blank line to separate the subject line from the body message.
