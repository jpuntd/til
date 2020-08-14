# Destructuring nested objects

We can destructure an object to get multiple properties at the same time...

```javascript
const { state, dispatch } = React.useContext(store);
```

We can also get a specific property of a nested object...

```javascript
const {
  state: { selection },
} = React.useContext(store);
console.log(selection);
```

And both combined...

```javascript
const {
  state,
  dispatch,
  state: { selection },
} = React.useContext(store);
```

This gives me **state**, **dispatch** and the **selection** property of state.
