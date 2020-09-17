# What is CSP (Content Security Policy)?

A browser security mechanism that restricts the resources a page can load.

Send a `Content-Security-Policy` header with one or more directives.

    Content-Security-Policy: default-src 'self' http://example.com;

Or include it in `meta` tag.

    <meta http-equiv="Content-Security-Policy" content="default-src https:">

Before implementation the `Content-Security-Policy-Report-Only` header can be used to report violations instead of preventing violations.
