# The clamp() function

    clamp(MIN, PREFERRED, MAX)

The clamp() CSS function takes three parameters: a minimum value, a preferred value, and a maximum allowed value.

```css
.parent {
  display: grid;
  place-items: center;
}
.card {
  width: clamp(23ch, 50%, 46ch);
  display: flex;
  flex-direction: column;
  padding: 1rem;
}
```

The `ch` unit is the width of the `0` character. Be ware that average character is wider.

[source](https://1linelayouts.glitch.me/)
