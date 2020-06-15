# Setting attribute or property of a html element

## using setAttribute

The attribute name is automatically converted to all lower-case when `setAttribute()` is called on an HTML element in an HTML document.

    const b = document.querySelector("button");

    b.setAttribute('disabled', '')
    b.setAttribute('disabled', false)
    b.setAttribute('disabled', "false")
    b.setAttribute('disabled', null)

All have the same result: a disabled button.

To remove an attribute, call `removeAttribute()`.

## set property of a html element

    b.disabled = '';
    b.disabled = false;
    b.disabled = null;

All falsy values. Result: button is **enabled**.

    b.disabled = 'false';

Evaluates to true. Result: button is **disabled**.

Setting the property is case sensitive. So

    inputElement.setAttribute('formMethod', 'post');
    inputElement.formmethod = 'post';

have the same result.
