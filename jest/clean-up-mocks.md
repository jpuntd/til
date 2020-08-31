# clean up mocks

You want to clean up a mock's usage data between two assertions. Jest has the following methods:

## mockFn.mockClear()

Resets all information stored in the mockFn.mock.calls and mockFn.mock.instances arrays.

## mockFn.mockReset()

Does everything that mockFn.mockClear() does, and also removes any mocked return values or implementations.

## mockFn.mockRestore()

Does everything that mockFn.mockReset() does, and also restores the original (non-mocked) implementation.
This only works when the mock was created with `jest.spyOn`, not when manually assigning jest.fn().

## The jest object has similar methods to clean up all mocks at once:

- jest.clearAllMocks()
- jest.resetAllMocks()
- jest.restoreAllMocks()

Use it with `afterEach`:

```javascript
afterEach(() => {
  mockContext.dispatch = null;
  container.unmount();

  jest.resetAllMocks();
});
```
