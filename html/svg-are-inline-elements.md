# svg are inline elements

## Difference in height of 5px

I had a SVG element (no height specified) inside of div (no height specified). But, the height value for parent div is 5px different from SVG.

## Explanation

SVG elements are inline elements, which are meant to render text, so some space is reserved underneath the element (below the baseline) for the letters descender.

## You can work around this in several ways:

Change it to block level element:

    svg {
        display: block;
    }

Eliminate the line height of the container:

    #parentelement {
        line-height: 0;
    }
