# implement IterableIterator interface

A value is iterable if it has a method that returns an iterator. The iterator is an object that returns values, one value per call to its method next().
In TypeScript notation:

```typescript
interface Iterable {
  [Symbol.iterator](): Iterator;
}
interface Iterator {
  next(): IteratorResult;
}
interface IteratorResult {
  value: any;
  done: boolean;
}
```

We can combine `Iterator` and `Iterable` interfaces. All ES6 iterables (Array, Set, ...) also implement Iterator.

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

[source](https://exploringjs.com/es6/ch_iteration.html#sec_iterability)
