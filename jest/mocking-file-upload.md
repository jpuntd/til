# mocking a file upload in jsdom

I did not succeed in mocking a file upload when testing a component with `<input type="file">`

Directly setting the `files` property of the input element comes close. This property is readonly. So setting files directly didn’t work. But `defineProperty` did.

```javascript
it('should show an error message when filesize is too large', () => {
  let uploadedFiles = [
    {
      name: 'letmeknife.jpg',
      size: 4455248,
      type: 'image/jpeg'
    },
    {
      name: 'knifemelet.jpg',
      size: 42248,
      type: 'image/jpeg'
    }
  ];

  // I have to do this because `input.files =[file1, file2]` is not allowed
  Object.defineProperty(element.shadowRoot.querySelector('input'), 'files', {
    value: uploadedFiles
  });

  element._validate();

  expect(element.shadowRoot.querySelector('.error').className).toContain('invalid');
});
```

[source](https://github.com/testing-library/react-testing-library/issues/93)
