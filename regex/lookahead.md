# lookahead and negative lookahead

Looking at the regular expression in the following svelte example.

```html
<script>
  import Keypad from "./Keypad.svelte";

  let pin;
  $: view = pin ? pin.replace(/\d(?!$)/g, "•") : "enter your pin";

  function handleSubmit() {
    alert(`submitted ${pin}`);
  }
</script>

<h1 style="color: {pin ? '#333' : '#ccc'}">{view}</h1>

<Keypad bind:value="{pin}" on:submit="{handleSubmit}" />
```

[source](https://svelte.dev/tutorial/component-bindings)

## Lookahead

Matches at a position where the pattern inside the lookahead can be matched. Matches only the position. It does not consume any characters or expand the match.
`t(?=s)` matches the second t in streets.

## Negative lookahead

Only succeeds if the regex inside the lookahead fails to match.
`t(?!s)` matches the first t in streets.

[source](https://www.regular-expressions.info/refadv.html)

## Explanation

So `\d(?!$)` matches a digit that is not the last character on the line.
As such it can be used to obfuscate every digit of our pin except the last entered.
