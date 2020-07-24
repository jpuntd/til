# Allow external styling of a part of a Custom Element

## Inside the template

Add a `part` attribute to those parts you want to be styled from the outside.

```html
<template id="tabbed-custom-element">
  <style type="text/css">
    :host {
      display: flex;
    }
  </style>
  <div part="tab active">Tab 1</div>
  <div part="tab">Tab 2</div>
  <div part="tab">Tab 3</div>
</template>
```

## Usage

Use the `::part` pseudoelement to refer to a part when styling from the outside.

```css
tabbed-custom-element::part(tab) {
  color: #0c0c0dcc;
  border-bottom: transparent solid 2px;
}

tabbed-custom-element::part(tab):hover {
  background-color: #0c0c0d19;
  border-color: #0c0c0d33;
}

tabbed-custom-element::part(tab):hover:active {
  background-color: #0c0c0d33;
}

tabbed-custom-element::part(tab):focus {
  box-shadow: 0 0 0 1px #0a84ff inset, 0 0 0 1px #0a84ff,
    0 0 0 4px rgba(10, 132, 255, 0.3);
}

tabbed-custom-element::part(active) {
  color: #0060df;
  border-color: #0a84ff !important;
}
```

[source](https://developer.mozilla.org/en-US/docs/Web/CSS/::part)
