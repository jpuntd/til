# private variables in ES6 classes

When we need more than the convention to use an underscore...

## use WeakMaps to map each instance to a private variable

    const _counter = new WeakMap();
    const _action = new WeakMap();

    class Countdown {
        constructor(counter, action) {
            _counter.set(this, counter);
            _action.set(this, action);
        }
        dec() {
            let counter = _counter.get(this);
            if (counter < 1) return;
            counter--;
            _counter.set(this, counter);
            if (counter === 0) {
                _action.get(this)();
            }
        }
    }

## use one WeakMap to map each instance to all the data that should be private

    const private_data = new WeakMap();

    class Countdown {
        constructor(counter, action) {
            const _private = new Map()
            .set('counter', counter)
            .set('action', action);
            private_data.set(this, _private);
        }
        dec() {
            const _private = private_data.get(this);
            let counter = _private.get('counter');
            if (counter < 1) return;
            counter--;
            _private.set('counter', counter);
            if (counter === 0) {
            _private.get('action')();
            }
        }
    }

## store private data inside properties whose keys are symbols:

    const _counter = Symbol('counter');
    const _action = Symbol('action');

    class Countdown {
        constructor(counter, action) {
            this[_counter] = counter;
            this[_action] = action;
        }
        dec() {
            if (this[_counter] < 1) return;
            this[_counter]--;
            if (this[_counter] === 0) {
                this[_action]();
            }
        }
    }

Symbols are not completely private. Reflect.ownKeys() also lists symbols.

    const c = new Countdown(2, () => console.log('DONE'));

    console.log(Object.keys(c));
        // []
    console.log(Reflect.ownKeys(c));
        // [ Symbol(counter), Symbol(action) ]

[source](https://exploringjs.com/es6/ch_classes.html#sec_private-data-for-classes)
