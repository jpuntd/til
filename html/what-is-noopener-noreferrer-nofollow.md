# What do noopener, noreferrer, nofollow mean?

They are used in links set to open in a new tab:

    <a href="https://www.site.com" rel="noopener noreferrer nofollow" target="_blank">Visit website.</a>

## noopener

When you are using target=" \_blank" value, the page you are linking to gets partial access to the linking page through the `window.opener` object. The linking page could then use `window.opener.location` to, for instance, display a malicious login form.

When you use `rel="noopener"`,`window.opener` will return `null`.

## noreferrer

The `noreferrer` value will hide referrer information when the link is clicked. Analytics software will show it as direct traffic, not as a referral.

## nofollow

The general rule is to use nofollow on low-quality links, like in user comments. You don’t want your website to pass its value to low-quality pages.
