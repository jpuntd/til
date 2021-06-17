# React by not using React

## Reimplement useState hook

function useState (initialState) {
  let value = initialState
  
  function setState (nextValue) {
    value = nextValue
    ReactDOM.render(<MyName />, document.getElementById('root'))
  }
  
  return [ value, setState ]
}

This works. But the render call makes it so that we cannot use it for an input field: the value gets reset.
