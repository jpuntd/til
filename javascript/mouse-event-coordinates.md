# Get coordinates of a mouse event

## offsetX and offsetY

provides the offset in the X coordinate of the mouse pointer between an event and the padding edge of the target node.

## pageX and pageY

measured relative to the top left of the whole page rendered in the browser. This reference point is below the URL bar and back button in the upper left.

## screenX and screenY

measured relative to the top left of the physical screen/monitor.

## clientX and clientY (is equal to event.x and event.y)

measured relative to the upper left edge of the content area (the viewport) of the browser window.
The MouseEvent.x property is an alias.

# movementX and movementY

provides the difference in the X coordinate of the mouse pointer between the given event and the previous mousemove event. In other words, the value of the property is computed like this: currentEvent.movementX = currentEvent.screenX - previousEvent.screenX.
