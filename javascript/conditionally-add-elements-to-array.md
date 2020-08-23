# Conditionally adding elements to array

We want to add items, **when they are defined**, to the following array.

```javascript
const hashInputArray = [param.name, quantiles.value, regions.value];
```

## Splice them in afterwards, based on a condition.

```javascript
if (standard) {
  hashInputArray.splice(2, 0, standard.value);
}

if (line) {
  hashInputArray.splice(2, 0, line.value);
}
```

## Use the array spread operator

Works because `...[]` will not add anything to the resulting array.

```javascript
const hashInputArray = [
  param.name,
  quantiles.value,
  ...(line ? [line.value] : []),
  ...(standard ? [standard.value] : []),
  regions.value,
];
```

## Use a helper function

```javascript
const valueIfDefined = (item) => (item ? [item.value] : []);
const hashInputArray = [
  param.name,
  quantiles.value,
  ...valueIfDefined(line),
  ...valueIfDefined(standard),
  regions.value,
];
```
