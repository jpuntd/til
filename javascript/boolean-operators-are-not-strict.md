# Boolean operators are not strict.

For instance they do not follow De Morgan's laws.

Trying to simplify the following return statement

```javascript
return !(!value || Object.keys(value).length === 0);
```

Of course we have De Morgan's laws...

```javascript
!(A && B) is equivalent to !A || !B
!(A || B) is equivalent to !A && !B
```

...suggesting this rewrite...

```javascript
return !!value && Object.keys(value).length !== 0;
```

But this causes an error when value is a primitive.

## Why De Morgan's laws don't work for the `&&` and `||` operator.

Logical operators `&&` and `||` in javascript use short-circuit evaluation.
Take the original return statement.

```javascript
return !(!value || Object.keys(value).length === 0);
```

It works because it stops evaluation of the expression as soon as `!value` evaluates to true.
That's why transforming it simply using De Morgan's laws is not possible.

Suggested alternative:

```javascript
return !!value || (value typeof 'object' && Object.keys(value).length);
```
