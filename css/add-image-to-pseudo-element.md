# Add an image to pseudo-element

Today I learned that you can do this directly inside `content`.

    div::before {
      content: url('assets/flash.png');
    }
