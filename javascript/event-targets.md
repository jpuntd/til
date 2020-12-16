# Event targets

## event.target

= the element that triggered the event (e.g., the user clicked on)

## event.currentTarget

= element where you attached event listener to

## event.relatedTarget

Identifies a secondary target for the event.

| Event name | target                                          | relatedTarget                                   |
| ---------- | ----------------------------------------------- | ----------------------------------------------- |
| mouseenter | The EventTarget the pointing device entered to  | The EventTarget the pointing device exited from |
| mouseleave | The EventTarget the pointing device exited from | The EventTarget the pointing device entered to  |
| mouseout   | The EventTarget the pointing device exited from | The EventTarget the pointing device entered to  |
| mouseover  | The EventTarget the pointing device entered to  | The EventTarget the pointing device exited from |
| dragenter  | The EventTarget the pointing device entered to  | The EventTarget the pointing device exited from |
| dragexit   | The EventTarget the pointing device exited from | The EventTarget the pointing device entered to  |

## event.composedTarget

The original non-native target of the event before composition from Shadow DOM.

[source](https://developer.mozilla.org/en-US/docs/Web/API/Event/Comparison_of_Event_Targets)
