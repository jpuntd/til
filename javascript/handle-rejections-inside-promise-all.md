# Handle rejections inside Promise.all

Promise.all is rejected if one the promises in the array is rejected.
Today I learned that this is not the case when every possible rejection is caught.

```javascript
const flakyApi = (resolve, reject) => {
  const wait = Math.random() * 1000;
  if (wait < 400) {
    setTimeout(() => resolve(`waited ${wait}ms for this result`), wait);
  } else {
    setTimeout(() => reject(`error after ${wait}ms`), wait);
  }
};
```

## Handle possible rejection for each promise

```javascript
let promise1 = new Promise(flakyApi);
let promise2 = new Promise(flakyApi);
let promise3 = new Promise(flakyApi);
let promise4 = new Promise(flakyApi);

Promise.all([
  promise1.catch((error) => error),
  promise2.catch((error) => error),
  promise3.catch((error) => error),
  promise4.catch((error) => error),
])
  .then(function (data) {
    data.forEach(function (data) {
      console.log(data); // will log all the data and errors
    });
  })
  .catch(function (error) {
    console.log(error);
  });
```

## Use Promise.allSettled()

The outcomes will be objects:

    { status: 'fulfilled', value: data }
    { status: 'rejected', reason: error }

```javascript
let promise1 = new Promise(flakyApi);
let promise2 = new Promise(flakyApi);
let promise3 = new Promise(flakyApi);
let promise4 = new Promise(flakyApi);

Promise.allSettled([promise1, promise2, promise3, promise4])
  .then(function (data) {
    data.forEach(function ({ status, reason = "", value = "" }) {
      console.log(status, reason, value);
    });
  })
  .catch(function (error) {
    console.log(error);
  });
```
