# Three forms of XSS.

## What is XSS

A cross-site-scripting attack happens when an attacker succeeds in injecting client-side scripts into web pages viewed by other users.

## Stored XSS

User input (eg a comment) that contains a script is not properly sanitized and stored in a database (or log) that is viewed at a later time by another user.

## Reflected XSS

A user is tricked into following a malicious link or submitting a form. The webserver _reflects_ the input it received back to the user's browser. A webserver could For instance echo a user provided search term back to the user. The search term could then be carefully crafted to inject code in the receiving webpage.

### DOM XSS

An attacker modifies the DOM “environment” in the victim’s browser used by a javascript framework or client side script, so that the client side code runs in an “unexpected” manner. Attacker could do this by tricking user into following a malicious link or submitting a form.

The problem is aggravated when client side code uses a template system to embed text in webpages. Modern browsers have filters that detect XSS attempts but they don't check template expressions that may also execute injected scripts.

[Cross Site Scripting Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)

[DOM based XSS Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/DOM_based_XSS_Prevention_Cheat_Sheet.html)
