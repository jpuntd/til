# Scale svg images

Raster images have a clearly defined size and aspect ratio.
You can set the height or the width, and the browser adjusts the other dimension.

We need to explicitly provide this information if you want a SVG to scale.

## Easy solution to scale preserving aspect ratio

SVG scales nicely if it has a viewBox, and is used as <img>.

## The viewbox attribute

    viewBox="0 0 100 100"

It defines the aspect ratio of the image.
It defines how all the lengths and coordinates used inside the SVG should be scaled to fit the total space available.
It defines the origin of the SVG coordinate system, the point where x=0 and y=0.

## The preserveAspectRatio attribute

    preserveAspectRatio="xMidYMid meet"

The `preserveAspectRatio` describes how the image should scale if the aspect ratio of the viewBox doesn’t match the aspect ratio of the viewport.

[source](https://css-tricks.com/scale-svg/)
