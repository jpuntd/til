# join elements to form a string when some elements are optional

We want to build a string from multiple elements: `one | two | three`

Some elements are optional. How to prevent it looking like `one | | three`?

## filter out falsy values before joining

    const category = legend.category ? translate(translations.category) : false;

    return [
        translate(translations.quantile),
        translate(translations.region),
        category
    ].filter(Boolean)
    .join(' | ');

## wrap optional elements in an array and destructure

    const category = legend.category ? [translate(translations.category)] : [];

    return [
        translate(translations.quantile),
        translate(translations.region),
        ...category
    ].join(' | ');
