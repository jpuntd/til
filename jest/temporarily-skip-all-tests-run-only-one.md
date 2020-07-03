# Temporarily skip all tests but one

I wanted to isolate one of the tests I was working on.
Turns out you can change `it` from the one test you are working on to read `it.only`. Or change `test` to `test.only`.
Jest will only run that test in that file.

```javascript
it.only("this will be the only test that runs", () => {
  expect(true).toBe(false);
});

it("this test will not run", () => {
  expect("A").toBe("A");
});
```

Today I learned that you can also use `fit` to <u>f</u>ocus on one test.

```javascript
fit("this will be the only test that runs", () => {
  expect(true).toBe(false);
});

it("this test will not run", () => {
  expect("A").toBe("A");
});
```

Same goes for `describe.only`.
