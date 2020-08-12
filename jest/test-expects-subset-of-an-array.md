# check for a subset of an array

Testing if function returns the right arguments, but it returns an array with a lot of items and we are only interested in part of them.

```javascript
it('should return result and norm for filter with norm', async () => {
    ...
    expect(firstCallResponse).toEqual( lots of things,  ['results', 'norms'], ['testFilter'], lots of things );
});
```

We can use `expect.arrayContaining` to make expect only care about the items we list up...

```javascript
it('should return result and norm for filter with norm', async () => {
    ...
    expect(firstCallResponse).toEqual(expect.arrayContaining([['results', 'norms'], ['testFilter']]));
});
```

[source](https://jestjs.io/docs/en/expect#expectarraycontainingarray)
