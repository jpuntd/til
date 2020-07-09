# transform property creates a new stacking context

A stacking context is an element that contains a set of layers. The z-index of children shows the relative position of a child **inside** that stacking context. Other elements outside the stacking context can't get in between the layers. The whole element is then put in the stacking order of the parent stacking context.

The <html> element creates a root stacking context. Every element with a position value `absolute` or `relative` and z-index set, creates a new stacking order.

Working on a React SlidingContainer component that uses `transform: translate`. Noticed that the `transform` property also creates a new stacking context.

## Some ways an element can become a stacking context:

- z-index set to a value on absolute, relative, fixed or sticky elements
- position value `fixed` or `sticky`
- opacity value other than 1
- element with transform or filter property set

## Use the z-context DevTools extension

Used it to display the parent stacking context for an element. Also displays the reason why a new stacking context was created.

[source](https://tiffanybbrown.com/2015/09/css-stacking-contexts-wtf/index.html)
