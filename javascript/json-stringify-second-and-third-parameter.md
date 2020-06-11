# JSON.stringify method has a second and third parameter

    JSON.stringify(value, replacer, space)

## space

A String or Number object that's used to insert white space into the output JSON string for readability purposes.

    JSON.stringify({ a: 2, b: { c:3 }}, null, '\t');
    JSON.stringify({ a: 2, b: { c:3 }}, null, 4);

## replacer array

A whitelist of properties included in the resulting string.

    JSON.stringify({ a: 2, b: { c:3 }}, ['b','c'], '\t');

## replacer function

A function that alters the behavior of the stringification process. I wanted to limit the stringification to one level deep and used the following...

    const oneLevelDeep = (key, value) =>
        key && value && typeof value !== 'number' ? value.toString() : value;

    JSON.stringify(obj, oneLevelDeep);
