# percentage value in transform

When setting width and height, an element's width and height are based on parent’s width and height.

Same for `left` and `top`. This will put `self` in bottom right corner of parent:

```css
.self {
  position: absolute;
  height: 50%;
  width: 50%;
  top: 50%;
  left: 50%;
}
```

But `transform: translate` percentage values are based on `self` element's width and height.

```css
.self {
  position: absolute;
  height: 50%;
  width: 50%;
  translate-top: 100%;
  translate-left: 100%;
  transform: translate(100%, 100%);
}
```

[source](https://wattenberger.com/blog/css-percents)
