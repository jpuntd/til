# What is the Michael Jackson Script file extension?

It is (jokingly) used to refer to the `.mjs` file extension.

## CommonJS / CJS specification

    exports.helloWorld = () => {
      console.log('hello world')
    }


    const { helloWorld } = require('foobar') 

Node.js executes `require` statements synchronously, just like the other code. The `shape` of the exported function(s) can only be determined after the code is executed.

## ES6 modules / ESM specification

    export function helloWorld () {
      console.log('hello world')
    }


    import { helloWorld } from 'foobar' 

When ES6 modules are loaded, they are first parsed to determine the _shape_ of the export. Then the runtime asynchronously loads imports and only then executes the code. 

## The `.mjs` file extension

Node.js will treat the following as ES modules:

- Files ending in `.mjs`. <-- the so called _Michael Jackson Script_ file extension
- Files ending in .js when the nearest parent package.json file contains a top-level field "type" with a value of "module".

Node.js will treat as CommonJS all other forms of input to preserve backward compatibility. If you want to be explicit, use the following for CommonJS:

- File extension `.cjs`.
- Top-level field "type" with a value of "commonjs" inside package.json.

[ESM in Node.js](https://nodejs.org/api/esm.html#esm_introduction)

[source](https://medium.com/the-node-js-collection/an-update-on-es6-modules-in-node-js-42c958b890c)



