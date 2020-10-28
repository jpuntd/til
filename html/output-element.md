# The output element

The HTML Output element (<output>) is a container element to display the results of a calculation or the outcome of a user action.

```html
<form oninput="result.value=parseInt(a.value)+parseInt(b.value)">
  <input type="range" id="b" name="b" value="50" /> +
  <input type="number" id="a" name="a" value="10" /> =
  <output name="result" for="a b">60</output>
</form>
```

Look at the `for` attribute indicating the elements that contributed input values.
The output element will automatically be an `aria-live` region.

[source](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/output)
