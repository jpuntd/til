# Remove the first three lines from a file.

I regularly download three files, remove the first 3 lines of the file and change some characters.
How to automate this using `sed`?

## Delete the first three lines

    sed -i '1,3d' lang.*.js

The `-i` flag means _edit in place_, so the lang.\*.js files get edited.

## Replace some characters

    sed -i 's/bol.lang = {/{/' lang.*.js

## Remove a character at the end of the last line

    sed -i 's/"};$/"}/' lang.*.js

Remove the `in place` flag to output the changes to stdout so you can see what is happening.
Pipe through `head` to see what you are changing at the beginning of the file.

    head -c 100 lang.en.js

will output the first 100 bytes of a file.
