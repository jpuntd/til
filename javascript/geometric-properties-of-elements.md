# Geometric properties of elements

## offsetParent

is the nearest positioned ancestor or td, th, table, body.

## offsetLeft/offsetTop

coordinates relative to the upper-left edge of offsetParent.

## offsetWidth/offsetHeight

the “outer” width/height of the element. Or, in other words, its full size including borders.

## clientLeft/clientTop

normally the border width.
the distances from the upper-left outer corner to the upper-left inner corner.
For right-to-left websites the vertical scrollbar is on the left so clientLeft includes its width too.

## clientWidth/clientHeight

the size of the area inside the element borders.
includes the content width together with paddings, but without the scrollbar

## scrollWidth/scrollHeight

the width/height of the content, just like clientWidth/clientHeight, but also include scrolled-out, invisible part of the element.

## scrollLeft/scrollTop

width/height of the scrolled out upper part of the element, starting from its upper-left corner.
In other words, scrollTop is “how much is scrolled up”.
