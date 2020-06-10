# the white-space property

The `white-space` property sets how white space inside an element is handled.

Have a CMS that sends you text with `\n` newline characters? Use

    white-space: pre-line;

Lines are broken at newline characters. But sequences of white space are collapsed.

If you want to completely mimic behaviour of the `<pre>` tag, use

    white-space: pre;

[Source](https://developer.mozilla.org/en-US/docs/Web/CSS/white-space)
