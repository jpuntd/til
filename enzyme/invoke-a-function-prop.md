# Invoke a function prop of a React component

Calling a function prop inside a test...

```javascript
container.find(myCombobox).first().prop("myonselect")({ value: "nl" });
```

This can be clearer expressed as ...

```javascript
container.find(myCombobox).first().invoke("myonselect")({ value: "nl" });
```

[source](https://enzymejs.github.io/enzyme/docs/api/ShallowWrapper/invoke.html)
