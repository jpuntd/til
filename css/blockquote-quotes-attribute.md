# blockquote quotes attribute

The `quotes` CSS property sets how the browser should render quotation marks that are added using the `open-quotes` or `close-quotes` values of the CSS `content` property.

```css
blockquote,
q {
  quotes: none;
}
```

```css
/* Keyword value */
quotes: none;
quotes: auto;

/* <string> values */
quotes: '«' '»'; /* Set open-quote and close-quote to the French quotation marks */
quotes: '«' '»' '‹' '›'; /* Set two levels of quotation marks */
```

```css
q {
  quotes: '"' '"' "'" "'";
}
q::before {
  content: open-quote;
}
q::after {
  content: close-quote;
}
```
