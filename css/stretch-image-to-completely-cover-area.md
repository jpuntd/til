# Stretch image to competely cover an area

## Set the image as background on a div.

Use `background-size: contain;` or `background-size: cover;`
Make sure to also set `background-repeat`;

```css
.bg-contain {
  background-image: url(https://picsum.photos/600/200);
  background-repeat: no-repeat;

  background-size: contain;
  background-position: center;
}
.bg-cover {
  background-image: url(https://picsum.photos/600/200);
  background-repeat: no-repeat;

  background-size: cover;
  background-position: right top;
}
```

## Style the img tag directly

Use `object-fit` and `object-position` directly on the `img` tag to achieve the same result.

```css
.image-contain {
  object-fit: contain;
  object-position: center;
}

.image-cover {
  object-fit: cover;
  object-position: right top;
}
```

[source](https://github.com/30-seconds/30-seconds-of-css/blob/master/snippets/fit-image-in-container.md)
