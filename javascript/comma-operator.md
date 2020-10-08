# The comma operator

I was looking at how TypeScript transpiles private properties of a class.

<details><summary>Short answer.</summary>Using a WeakMap to store the private data for each instance of the class.
It also follows the convention of prefixing the private members with underscore. So `_min` and `_max` are private in the following code.</details>

## Typescript example

```typescript
class NumberRange implements IterableIterator<number | undefined> {
  #min = 0;
  #max = 9;

  constructor(min: number, max: number) {
    this.#min = min;
    this.#max = max;
  }

  next() {
    return this.#min <= this.#max
      ? { done: false, value: this.#min++ }
      : { done: true, value: undefined };
  }

  [Symbol.iterator]() {
    return this;
  }
}

let s = new NumberRange(4, 6);
console.log([...s]);
```

## Transpiled code:

```javascript
var _min, _max;
class NumberRange {
  constructor(min, max) {
    // ...
  }
  [((_min = new WeakMap()), (_max = new WeakMap()), Symbol.iterator)]() {
    return this;
  }
}
```

[complete TypeScript code and transpiled code](https://www.typescriptlang.org/play/?ssl=24&ssc=1&pln=1&pc=1#code/MYGwhgzhAEByCuBbARgUwE4CUwDsDmq0AlogA4iqKo4AuMAkjRmMhY8zQPboA8OSadAB94OACaoAZkRyoxAPmgBvALAAoaNADEiGdAC80AAwBudZp1gAHgegBOM2vPRgnHBBrp4wLugAUujgAXPwoGAA00IjWIQIYAJTKzpo0ABZEEAB0OnqGgY6aKelZljZ51gXQAL7qzrJWNH6JqhqF6Kg08Og40GkZ2YHQPIZ9JdFWyYUA-MrQYm6oQdCSYCAQqJEAbqvwi73FAzIA1EfVk5pLSnMLS567Wzt7ohLSsmJnrTVOrQDaAMoATxQnBAmSITHQYF8AF0mklWpp2p1uvsMpUvl91BQaNAYIZZAB3OBxLC4Ah+AAs4QAbPFHK53CDUJkQJw8H4fpkuRBofFamogA)

## Use of the comma operator

> The comma operator `(,)` evaluates each of its operands (from left to right) and returns the value of the last operand. (MDN)

Notice how the following lines use the comma operator. The last value is returned and used as the computed property.

```javascript
[((_min = new WeakMap()), (_max = new WeakMap()), Symbol.iterator)]() {
  return this;
}
```

This unravels to

```javascript
_min = new WeakMap();
_max = new WeakMap();
[Symbol.iterator]() {
  return this;
}
```
