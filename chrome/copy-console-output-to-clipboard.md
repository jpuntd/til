# take value you logged to the console and copy to clipboard

When a `console.log` outputs a large object to the Google Chrome console, you can copy it to the clipboard.

- Right-click the output of the `console.log` statement.
- Select the _Store as a global variable option_
- Chrome will store the output in a global variable.
- Chrome displays the name in the console: `temp1`
- use the following command to copy it to the clipboard:

  copy(temp1);

This also works for `console.dir` or `console.table` or inside React Devtools, etc...
