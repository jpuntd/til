# optional and required parameters in a function

Scenario: Set the required **and** the last optional parameter

## 1 required parameter and 5 optional parameters

```javascript
function alphaNumV1(required, a = 1, b = 2, c = 3, d = 4, e = 5, f = 12) {
  console.log(required, a, b, c, d, e, f);
}

alphaNumV1('banana', undefined, undefined, undefined, undefined, undefined, 6);
```

We must set ALL of the preceding "optional" parameters to undefined.

## 1 required parameter and 5 optional parameters in an optional config object

```javascript
function alphaNumV2(required, obj = { a: 1, b: 2, c: 3, d: 4, e: 5, f: 12 }) {
  console.log(required, obj.a, obj.b, obj.c, obj.d, obj.e, obj.f);
}

alphaNumV2('bananas', { f: 6 });
```

Result: FAIL.

Explanation: Although the config object is optional and
has defaults set for every option, we cannot change a
single option. The config object that we pass
in overwrites the default config object.

## 1 required parameter and 5 OPTIONAL parameters in a REQUIRED config object

```javascript
function alphaNumV3(required, { a: a = 1, b: b = 2, c: c = 3, d: d = 4, e: e = 5, f: f = 12 }) {
  console.log(required, a, b, c, d, e, f);
}

alphaNumV3('bananas', { f: 6 });

try {
  alphaNumV3('bananas');
} catch (err) {
  console.log(err.message); // Cannot read property 'a' of undefined
}
```

Result: FAIL

Explanation: Although the second object parameter
contains OPTIONAL parameters only, the object
parameter itself is NOT optional

## 1 required parameter and 5 OPTIONAL parameters in an OPTIONAL config object

```javascript
function alphaNumV4(required, { a = 1, b = 2, c = 3, d = 4, e = 5, f = 12 } = {}) {
  console.log(required, a, b, c, d, e, f);
}

alphaNumV4('bananas');
alphaNumV4('bananas', { f: 6 });
```

Result: OK
