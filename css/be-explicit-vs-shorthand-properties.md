# shorthand properties versus being explicit

Writing `background: white;` will effectively result in all these properties being set:

```css
background-color: white;
background-image: none;
background-position: 0% 0%;
background-size: auto auto;
background-repeat: repeat;
background-origin: padding-box;
background-clip: border-box;
background-attachment: scroll;
```

It's better to be explicit. If you want to change the background color, use `background-color`.

[source](https://mxb.dev/blog/the-css-mindset/)
