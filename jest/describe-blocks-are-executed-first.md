# Order of execution of describe and test blocks

The following test succeeds when run in isolation, fails when run together with other tests.

```javascript
describe("select all", () => {
  const postFilterSpy = jest
    .spyOn(orchestrator, "postData")
    .mockImplementation(Promise.resolve);

  it.only("should ...", () => {
    // ...

    expect(postFilterSpy).toHaveBeenCalledTimes(1);
  });
});
```

When we ran the whole testsuite the postData mock method was called multiple times. We didn’t take into account that Jest executes all the describe blocks in a test file before any of the actual tests. [Jest documentation](https://jestjs.io/docs/en/setup-teardown#order-of-execution-of-describe-and-test-blocks).

We created `postFilterSpy` before all the tests ran.

During the tests the save button was clicked 3 times, each time calling **the same** `postFilterSpy` mock method and thus throwing off the number of times the mock method had been called.

## How to diagnose?

The test failed when a new test was added or when ran in isolation. Clearly a sign that other tests were influencing this test.

Use `test.only()` or `it.only()` to run a test in isolation.

## How to prevent?

Setup and teardown `postFilterSpy` for each test.

```javascript
  describe('select all', () => {
    let postFilterSpy;

    beforeEach(() => {
      postFilterSpy = jest.spyOn(orchestrator, 'postData').mockImplementation(Promise.resolve);
    });

    afterEach(() => {
      postFilterSpy.mockRestore();
    });
```
