# Zero-fill right shift and indexOf

Found the following in [mitt](https://github.com/developit/mitt/blob/master/src/index.ts):

```typescript
/**
 * Remove an event handler for the given type.
 * @param {string|symbol} type Type of event to unregister `handler` from, or `"*"`
 * @param {Function} handler Handler function to remove
 * @memberOf mitt
 */
off<T = any>(type: EventType, handler: Handler<T>) {
	const handlers = all.get(type);
	if (handlers) {
		handlers.splice(handlers.indexOf(handler) >>> 0, 1);
	}
},
```

`indexOf` returns -1 when `handler` can't be found inside `handlers`. We can convert it to an unsigned int using `>>> 0`.

    -1 >>> 0 === 4294967295 === 2 ** 32 - 1

This means it is now safe to use splice on it (unless `handlers` has 4294967295 items.)
