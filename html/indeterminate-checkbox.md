# indeterminate checkbox

There is no `indeterminate` attribute. It is a property of checkboxes. So you have to change it via JavaScript.

    var checkbox = document.getElementById("some-checkbox");
    checkbox.indeterminate = true;

The indeterminate state is **visual only**. The checkbox is still either checked or unchecked as a state.

[source](https://css-tricks.com/indeterminate-checkboxes/)
