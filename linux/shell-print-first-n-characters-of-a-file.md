# show first n characters of a file

`head` and `tail` also have a character flag.

    head -c 100 lang.en.js

will output the first 100 bytes of a file.

You can also pipe through `head` to see what for instance a sed command is changing at the beginning of a file.

    sed '1,3d' lang.en.js | head -c 50
