---
title: Web Components
category: JavaScript
layout: 2017/sheet
updated: 2020-06-22
weight: -10
intro: |
  [Vue.js](https://vuejs.org/) is an open-source Model–view–viewmodel JavaScript framework for building user interfaces and single-page applications.
---

{%raw%}

## Expressions

{: .-three-column}

### Expressions

```html
<div id="app">
  <p>I have a {{ product }}</p>
  <p>{{ product + 's' }}</p>
  <p>{{ isWorking ? 'YES' : 'NO' }}</p>
  <p>{{ product.getSalePrice() }}</p>
</div>
```

#### Two-way data binding

```html
<input v-model="firstName" />
```

| Method                 | Description                    |
| ---------------------- | ------------------------------ |
| `v-model.lazy="..."`   | Syncs input after change event |
| `v-model.number="..."` | Always returns a number        |
| `v-model.trim="..."`   | Strips whitespace              |

See: [Directives](https://vuejs.org/v2/api/#Directives)

### Actions/Events

#### Calls addToCart method on component

```html
<button v-on:click="addToCart">...</button>
```

#### Shorthand syntax

```html
<button @click="addToCart">...</button>
```

{: data-line="1"}

#### Arguments can be passed

```html
<button @click="addToCart(product)">... }</button>
```

#### To prevent default behavior (e.g. page reload)

```html
<form @submit.prevent="addProduct">...</form>
```

#### Only trigger once

```html
<img @mouseover.once="showImage" />...
```

| Method  | Description                                    |
| ------- | ---------------------------------------------- |
| `.stop` | Stop all event propagation                     |
| `.self` | Only trigger if event.target is element itself |

#### Keyboard entry example

```html
<input @keyup.enter="submit" />
```

#### Call onCopy when control-c is pressed

```html
<input @keyup.ctrl.c="onCopy" />
```

See: [Events](https://vuejs.org/v2/guide/events.html)

### List rendering

#### The `:key` is always recommended

```html
<li v-for="item in items" :key="item.id">
  {{ item }}
</li>
```

{: data-line="2"}

#### To access the position in the array

```html
<li v-for="(item, index) in items">...</li>
```

#### To iterate through objects

```html
<li v-for="(value, key) in object">...</li>
```

#### Using `v-for` with a component

```html
<cart-product
  v-for="item in products"
  :product="item"
  :key="item.id"
></cart-product>
```

See: [List Rendering](https://vuejs.org/v2/guide/list.html)

## Component

### Component anatomy

```js
class AppDrawer extends HTMLElement {

  // A getter/setter for an open property.
  get open() {
    return this.hasAttribute('open');
  }

  set open(val) {
    // Reflect the value of the open property as an HTML attribute.
    if (val) {
      this.setAttribute('open', '');
    } else {
      this.removeAttribute('open');
    }
    this.toggleDrawer();
  }

  // A getter/setter for a disabled property.
  get disabled() {
    return this.hasAttribute('disabled');
  }

  set disabled(val) {
    // Reflect the value of the disabled property as an HTML attribute.
    if (val) {
      this.setAttribute('disabled', '');
    } else {
      this.removeAttribute('disabled');
    }
  }

  // Can define constructor arguments if you wish.
  constructor() {
    // If you define a constructor, always call super() first!
    // This is specific to CE and required by the spec.
    super();

    // Setup a click listener on <app-drawer> itself.
    this.addEventListener('click', e => {
      // Don't toggle the drawer if it's disabled.
      if (this.disabled) {
        return;
      }
      this.toggleDrawer();
    });
  }

  toggleDrawer() {
    ...
  }
}

customElements.define('app-drawer', AppDrawer);
Vue.component('my-component', {
  components: {
    // Components that can be used in the template
    ProductComponent,
    ReviewComponent
  },
  props: {
    // The parameters the component accepts
    message: String,
    product: Object,
    email: {
      type: String,
      required: true,
      default: "none"
      validator: function (value) {
        // Should return true if value is valid
      }
    }
  },
  data: function() {
    // `data` must be a function
    return {
      firstName: 'Vue',
      lastName: 'Mastery'
    }
  },
  computed: {
    // Return cached values until dependencies change
    fullName: function () {
      return this.firstName + ' ' + this.lastName
    }
  },
  watch: {
    // Called when firstName changes value
    firstName: function (value, oldValue) { ... }
  },
  methods: { ... },
  template: '<span>{{ message }}</span>',
  // Can also use backticks in `template` for multi-line
})
```

{: data-line="3, 8, 16, 21, 28, 34, 39"}

See: [Components Basics](https://vuejs.org/v2/guide/components.html)

### Lifecycle hooks (or custom element reactions)

| Method                     | Description                                                                                                 |
| -------------------------- | ----------------------------------------------------------------------------------------------------------- |
| `constructor`              | Called when an instance of the element is created.                                                          |
| `connectedCallback`        | Called when the element is added to the DOM.                                                                |
| `disconnectedCallback`     | Called when the element is removed from the DOM.                                                            |
| `attributeChangedCallback` | Called when one of the attributes in the `observedAttributes` whitelist has been added, removed or updated. |
| `adoptedCallback`          | Called when the element has been moved into a new document.                                                 |

See: [Custom element reactions](https://developers.google.com/web/fundamentals/web-components/customelements#reactions)

### Custom events

#### Set listener on component, within its parent

```html
<button-counter v-on:incrementBy="incWithVal"></button-counter>
```

#### Inside parent component

```js
methods: {
  incWithVal: function (toAdd) { ... }
}
```

#### Inside button-counter template

```js
this.$emit(
  "incrementBy", // Custom event name
  5 // Data sent up to parent
);
```

Use props to pass data into child components,
custom events to pass data to parent elements.

See: [Custom Events](https://vuejs.org/v2/guide/components-custom-events.html)

## Single file components

### Single file

```html
<template>
  <p>{{ greeting }} World!</p>
</template>

<script>
  module.exports = {
    data: function () {
      return {
        greeting: "Hello",
      };
    },
  };
</script>

<style scoped>
  p {
    font-size: 2em;
    text-align: center;
  }
</style>
```

See: [Single File Components](https://vuejs.org/v2/guide/single-file-components.html)

### Separation

```html
<template>
  <div>This will be pre-compiled</div>
</template>
<script src="./my-component.js"></script>
<style src="./my-component.css"></style>
```

See: [What About Separation of Concerns?](https://vuejs.org/v2/guide/single-file-components.html#What-About-Separation-of-Concerns)

## Slots

### Using a single slot

#### Component template

```html
<div>
  <h2>I'm a title</h2>
  <slot>
    <!-- will be replaced by content from slot -->
  </slot>
</div>
```

{: data-line="3,4"}

#### Use of component with data for slot

```html
<my-component>
  <p>This will go in the slot</p>
</my-component>
```

{: data-line="2"}

### Multiple slots

#### Component template

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

{: data-line="3,6,9"}

#### Use of component with data for slots

```html
<app-layout>
  <h1 slot="header">Page title</h1>
  <p>the main content.</p>
  <p slot="footer">Contact info</p>
</app-layout>
```

{: data-line="2,3,4"}

See: [Adding flexibility with slots](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_templates_and_slots#Adding_flexibility_with_slots)

{%endraw%}
