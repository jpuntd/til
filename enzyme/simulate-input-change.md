# simulate changing the value of an inputfield

Call the simulate method and pass the event object.

```javascript
container
  .find('input[type="number"]')
  .first()
  .simulate("change", { target: { value: 2 } });
```
