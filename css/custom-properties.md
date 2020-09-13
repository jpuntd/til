# Custom properties vs css (static) variables

Better not to think of custom properties as variables in the sense of sass or less. These are static and can be used everywhere.
Custom properties are tied to a selector, although this can be the :root selector.

A custom property is tied to a selector and if the value changes, this affects all matching DOM elements just like any other CSS property.

```css
a {
  --link-color: black;
}
a:hover,
a:focus {
  --link-color: tomato;
}
@media screen and (min-width: 600px) {
  a {
    --link-color: blue;
  }
}

a {
  color: var(--link-color);
}
```

> Custom properties make sense when we have CSS properties that change relative to a condition in the DOM — especially a dynamic condition such as :focus, :hover, media queries or with JavaScript.

[source](https://www.smashingmagazine.com/2018/05/css-custom-properties-strategy-guide/)
