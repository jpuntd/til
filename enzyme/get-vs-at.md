# get node at a certain index

- `.get(index)` returns a ReactElement
- `.at(index)` returns a ReactWrapper

This returns a ReactWrapper or ShallowWrapper around the node at a given index of the current wrapper. So you can use it in Enzyme.

```javascript
const comboboxes = container.find(MyCombobox);
comboboxes.at(0).invoke("myonselect")({ value: "nl" });
```
