# Initialize State Lazily

If your init code has to do some heavy work, like mapping/filtering/reducing an array, don't put it inside your component, because it will get executed on every render.
You can wrap that initialization in a function and it will only run once:

```javascript
const [products, setProducts] = useState(() => {
  return hugeListOfProducts.filter(isOnSale);
});
```

The argument to the useState hook is disregarded on subsequent renders.

[source](https://reactjs.org/docs/hooks-reference.html#lazy-initial-state)
