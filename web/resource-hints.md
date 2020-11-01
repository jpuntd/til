# Resource hints

## Preload

Ideal for late-discovered resources like ...

- Fonts referenced inside a CSS file
- Critical resources dynamically loaded by JavaScript
- Content that only appears after an API call is made

```html
<link rel="preload" href="resources/roboto.woff" as="font" crossorigin="anonymous" />
```

resource hints like `preconnect` or `dns-prefetch` are hints the browser can choose to follow, preload hints are **required** to be executed.

## Preconnect

Tells the browser to make a proactive HTTP connection to a domain the browser will need later. This of course includes a DNS lookup.

```html
<link rel="preconnect" href="https://fonts.googleapis.com/" />
```

- browsers limit the number of HTTP connects they will maintain,
- browsers will close an HTTP connection if no requests happen within 10 seconds, so don't request a preconnect prematurely

## DNS Prefetch

A DNS Prefetch is a resource hint to make a DNS lookup (not a HTTP connection) for a domain the browser will need later.

```html
<link rel="dns-prefetch" href="https://stats.example.com/" />
```

[source](https://rigor.com/blog/what-are-preload-resource-hints/)
