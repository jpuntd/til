# create an array with numbers 1 to n

## numbers from 0 to n, n not included

    Array.from(Array(10).keys())
    //=> [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

or

    [...Array(10).keys()]

## numbers from 1 to n, n included

Pass a mapping function to Array.prototype.from

    Array.from(Array(10), (value,index) => index+1)

The Array.from() method creates a new, shallow-copied Array instance from an array-like or iterable object. So this is also possible...

    Array.from({ length: 10 }, (value,index) => index+1)

or perhaps more readable

    Array.from(Array(11).keys()).slice(1)
