# Using enum as bitfield

```typescript
enum TextDecorations {
  None,
  Bold = 1,
  Underline = 2,
  Italic = 4
}

let myTextStyle:TextDecorations = TextDecorations.Bold & TextDecorations.Italic;
```

Now we can check if myText is Bold.

```typescript
if (myTextStyle & TextDecorations.Bold === TextDecorations.Bold) {
  // ...
}
```

And we can toggle the 'underline style' bit without disturbing others.

```typescript
  myTextStyle |= TextDecorations.Underline;  // on

  myTextStyle &= ~TextDecorations.Underline;  // off
  // perform bitwise and with the negation of the underline bit
```
