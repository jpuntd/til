# The Module Pattern and Revealing Module Pattern

## Module Pattern

- Private members live in the closure.
- Public members are exposed in the return object.
- Parentheses around the anonymous function are a convention, not necessary. Assignement already makes sure the compiler interprets the function as a function expression

```javascript
const myModule = (function () {
  let myPrivateVar = 0;
  let myPrivateMethod = function (foo) {
    console.log(foo);
  };

  return {
    myPublicVar: "foo",
    myPublicFunction: function (bar) {
      myPrivateVar++;
      myPrivateMethod(bar);
    },
  };
})();
```

## Revealing Module Pattern

Also uses an <abbr title="immediately-invoked function expression">IIFE</abbr> to lock in values.
This variation has the advantage that public and private properties and methods are written in exactly the same way. We return an object with the properties and methods we want to _reveal_ as public (even possibly reveal under another name).

```javascript
const myRevealingModule = (function () {
    let privateVar = "Ben Cherry",
    let publicVar  = "Hey there!";
    function privateFunction() {
        console.log( "Name:" + privateVar );
    }
    function publicSetName( strName ) {
        privateVar = strName;
    }
    function publicGetName() {
        privateFunction();
    }

    return {
        setName: publicSetName,
        greeting: publicVar,
        getName: publicGetName
    };
})();
```

[Original post by Heilmann](https://christianheilmann.com/2007/08/22/again-with-the-module-pattern-reveal-something-to-the-world/)
