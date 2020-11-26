# Focus trap for a11y

When showing a modal, we hide the background webpage so users can't click on items. Keyboard users can however still activate other links.
Make sure users can't use the tab key to tab out of modal and activate other links.
Use the following selector to get all the elements that can be tabbed to:

    "button, [href], input, select, textarea, [tabindex]:not([tabindex="-1"])"

```javascript
const tabKeycode = 9;

function loopFocus(event) {
  if (event.keyCode === tabKeycode) {
    if (!event.shiftKey && document.activeElement === containerLastFocusable) {
      event.preventDefault();
      containerFirstFocusable.focus();
    } else if (event.shiftKey && document.activeElement === containerFirstFocusable) {
      event.preventDefault();
      containerLastFocusable.focus();
    }
  }
}

modal.addEventListener('keydown', loopFocus);
```

[source](https://github.com/tidave85/a11y-focus-trap/blob/master/index.js)
