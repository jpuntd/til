# Mutable module internal state pattern

## Inside a module

Export state and export a public function to mutate state inside a javascript module, eg `counter.js`

```javascript
export let count = 0;
export function increment() {
  count++;
}
```

## Import the module

Now its internal state can only be mutated through the exported function.

```javascript
import { count, increment } from './counter.js';
console.log(count); // prints 0
increment();
console.log(count); // prints 1
count++; // causes an error
```

The last line causes the following error: `TypeError: Assignment to constant variable!`

Why do we get that error?

> In ES6, imports are live read-only views on exported values (...)
> Unqualified imports are like const-declared variables.
> The properties of a module object are like the properties of a frozen object.
> [source](https://exploringjs.com/es6/ch_modules.html#_in-es6-imports-are-live-read-only-views-on-exported-values)

## Import only public functions

The `count` variable is essentially hidden and can only be mutated through the public functions that are exported.

Let's add a public function to log the `count` variable.
And remove the export for the `count` variable.

```javascript
let count = 0;
export function increment() {
  count++;
}
export function logCount() {
  console.log(count);
}
```

Then we can import only the public functions

```javascript
import { logCount, increment } from './counter.js';
logCount(); // prints 0
increment();
logCount(); // prints 1
console.log(count); // ReferenceError: count is not defined
```

[source](https://www.swyx.io/til-node-fundamentals-design-patterns-book/#2-module-design-patterns)
