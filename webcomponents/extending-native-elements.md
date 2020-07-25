# Extending native elements

## Extend from a specific HTMLElement.

```javascript
class MyButton extends HTMLButtonElement {
  constructor() {
    super();
  }
  ...
}
customElements.define('my-button', MyButton, {extends: 'button'});

```

The `{extends: 'button'}` is necessary because there may be multiple HTML elements sharing the same interface.

## Use with the `is` attribute.

```html
<button is="my-button"></button>
```

## Differences

- browsers without Custom Elements support will use native element
- trying to create a shadow root will throw an error.
