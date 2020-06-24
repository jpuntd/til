# use slot to allow markup from inside in your custom element

Today I learned that the syntax for slots in web component templates is exactly the same as the syntax Vue uses.

## Using a single slot

### Component template

```html
<div>
  <h2>I'm a title</h2>
  <slot>
    <!-- will be replaced by content from slot -->
  </slot>
</div>
```

### Use of component with data for slot

```html
<my-component>
  <p>This will go in the slot</p>
</my-component>
```

## Multiple slots

### Component template

```html
<div class="container">
  <header>
    <slot name="header"></slot>
  </header>
  <main>
    <slot>Default content when no slot is provided.</slot>
  </main>
  <footer>
    <slot name="footer">default content for footer slot</slot>
  </footer>
</div>
```

### Use of component with data for slots

```html
<app-layout>
  <h1 slot="header">Page title</h1>
  <p>the main content.</p>
  <p slot="footer">Contact info</p>
</app-layout>
```

See: [Adding flexibility with slots](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_templates_and_slots#Adding_flexibility_with_slots)

[source](https://devhints.io/vue#slots)
