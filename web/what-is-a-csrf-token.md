# what is a CSRF Token?

A token used to prevent a <abbr title="Cross-site request forgery">CSRF</abbr> attack.
The token should be:

- completely random
- tied to the user's session.
- sent together with the request so it can be used to validate before the relevant action is executed.

[source](https://portswigger.net/web-security/csrf)
