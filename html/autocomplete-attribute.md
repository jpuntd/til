# the autocomplete attribute

The HTML autocomplete attribute is available on `<input>` elements that take a text or numeric value as input, `<textarea>` elements, `<select>` elements, and `<form>` elements.

It can be used to set whether the browser is allowed to autocomplete form fields. Today I learned that it is not a boolean.

    autocomplete="off"
    autocomplete="on"

It takes a string that can be used to offer guidance to the browser as to the type of information expected in the field.

    autocomplete="family-name"
    autocomplete="country"

See [source](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/autocomplete#Values) for a complete list.
