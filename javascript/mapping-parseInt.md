# mapping parseInt

Today I learned why

    ['1','34','11'].map(parseInt)

is equal to

    [1, NaN, 3]

The callback function passed to `.map()` has the following signature:

    (value, index, array) => result

ParseInt takes only two arguments: string and radix.
So for the second item `parseInt` is called like this...

    parseInt('34', 1)

The symbols '3' and '4' do not exist in number systems with radix 2. So result is NaN.

For the third item `parseInt` is called like this...

    parseInt('11', 2)

Result is 3.
