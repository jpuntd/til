# Properties and attributes in custom elements

## Attributes

- provided in HTML
- only scalar values: string, number, and boolean

## Properties

- available when handling a DOM node in JavaScript
- can hold objects and arrays as well

## Reflect properties and attributes in custom elements

Most properties reflect their values as attributes. To do the same in your own class...

    export class RatingStars extends HTMLElement {

        get maxRating() {
            // cast to number
            return +this.getAttribute('max-rating');
        }

        set maxRating(value) {
            this.setAttribute('max-rating', value);
        }
    }

[source](https://www.thinktecture.com/en/web-components/native-web-components-without-framework/)
