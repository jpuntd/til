# More complex conditionals in switch statement

Most of the time `case` statements have simple values and the value passed to `switch` is used to compare with.

```javascript
switch (formType) {
  case types.checkbox:
    return createCheckbox(filterControlType, filterOptions);
  case types.combobox:
    return createCombobox(filterControlType, filterOptions);
  default:
    return null;
}
```

If we pass `true` as the value to compare with, we can add more complex conditionals.

```javascript
switch (true) {
  case typeof firstRow[orderState.key] === TableConfig.DATATYPE_UNDEFINED &&
    typeof secondRow[orderState.key] === TableConfig.DATATYPE_UNDEFINED:
    result = 0;
    break;
  case typeof firstRow[orderState.key] === TableConfig.DATATYPE_UNDEFINED:
    result = 1;
    break;
  case typeof secondRow[orderState.key] === TableConfig.DATATYPE_UNDEFINED:
    result = -1;
    break;
  case typeof firstRow[orderState.key] === TableConfig.DATATYPE_NUMBER:
    result = firstRow[orderState.key] - secondRow[orderState.key];
    break;
  case typeof secondRow[orderState.key] === TableConfig.DATATYPE_STRING:
    result = firstRow[orderState.key] < secondRow[orderState.key] ? -1 : 1;
    break;
  default:
    result = 0;
}
```
