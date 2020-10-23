# Use .tap(fn) to debug a test

`.tap(fn)` calls a function and then returns itself so it can be chained.

## Example

```javascript
container.find(MyCombobox).at(0).invoke('myonselect')({ value: 'nl' });
```

We want to get more information on the first combobox.

```javascript
container
  .find(MyCombobox)
  .at(0)
  .tap((node) => console.log(node.debug()))
  .invoke('myonselect')({ value: 'nl' });
```
