# convert string to array

Use array spread when string contains unicode characters

```javascript
"this will go wrong 🤔".split("");
// ["t", "h", "i", "s", " ", "w", "i", "l", "l", " ", "g", "o", " ", "w", "r", "o", "n", "g", " ", "�", "�"]
```

```javascript
[..."this will not go wrong 🤔"];
// ["t", "h", "i", "s", " ", "w", "i", "l", "l", " ", "n", "o", "t", " ", "g", "o", " ", "w", "r", "o", "n", "g", " ", "🤔"]
```
