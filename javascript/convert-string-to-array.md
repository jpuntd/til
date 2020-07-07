# convert string to array

Use array spread when string contains unicode characters.

```javascript
"will go wrong 🤔".split("");
// ["w", "i", "l", "l", " ", "g", "o", " ", "w", "r", "o", "n", "g", " ", "�", "�"]
```

```javascript
[..."will not go wrong 🙂"];
// ["w", "i", "l", "l", " ", "n", "o", "t", " ", "g", "o", " ", "w", "r", "o", "n", "g", " ", "🙂"]
```
