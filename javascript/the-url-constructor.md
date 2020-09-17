# The url constructor

Can be used to construct a valid(!) url.

## From a relative url and a base

```javascript
new URL("/en-US/docs", "https://developer.mozilla.org"); // => 'https://developer.mozilla.org/en-US/docs'
new URL("/en-US/docs", "https://developer.mozilla.org/fr-FR/toto"); // => 'https://developer.mozilla.org/en-US/docs'
```

## base is not used when first argument is an absolute url

```javascript
new URL("http://www.example.com"); // => 'http://www.example.com/'
new URL("http://www.example.com", "https://www.mozilla.org"); // => 'http://www.example.com/'
```

## raises an error when not a valid url

```javascript
new URL("/en-US/docs", ""); // Raises a TypeError exception as '' is not a valid URL
new URL("/en-US/docs"); // Raises a TypeError exception as '/en-US/docs' is not a valid URL
```

## first argument can also be a protocol relative url

```javascript
new URL("//foo.com", "https://example.com"); // => 'https://foo.com'
new URL("//foo.com", "http://example.com"); // => 'http://foo.com'
```

A protocol relative URL is just a URL without the scheme. If the browser is viewing that current page through HTTPS, then it’ll request that asset with the HTTPS protocol, otherwise it’ll request it with HTTP. [Security problems with protocol relative urls.](https://www.paulirish.com/2010/the-protocol-relative-url/)
