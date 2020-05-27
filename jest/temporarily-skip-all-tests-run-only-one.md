# Temporarily skip all tests but one

I wanted to isolate one of the tests I was working on. Normally I would replace all the `it`s in the test with `xit` and then enable the test I am working on.
Turns out you can change `it` from the one test you are working on to read `it.only`.
Jest will only run that test in that file.

```
it.only('this will be the only test that runs', () => {
 expect(true).toBe(false);
});

it('this test will not run', () => {
 expect('A').toBe('A');
});
```

Same goes for `describe.only`.
