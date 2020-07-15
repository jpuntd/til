# Use .tap(fn) to debug a test

`.tap(fn)` calls a function and then returns itself so it can be chained.

## Example

```javascript
container.find(PhyCombobox).at(0).invoke("phyonselect")({ value: "nl" });
```

We want to get more information on the first combobox.

```javascript
container
  .find(PhyCombobox)
  .at(0)
  .tap((node) => console.log(node.debug()))
  .invoke("phyonselect")({ value: "nl" });
```
