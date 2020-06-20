# setTimeout is not part of Javascript

> JavaScript Environment = JavaScript Runtime + Event Loop + Callback Queue + External API (eg WebAPI's)

Today I learned that setTimeout is part of the Web API provided by the Browser to the JavaScript Engine. Just like DOM, Fetch, History, Service Workers and Web Storage APIs.

Makes sense because Javascript is a fundamentally single threaded, synchronous language.
Any parts that are asynchronous (setTimeout, setInterval etc.) are implemented by and work via the execution environment.

[source](https://medium.com/swlh/console-log-isnt-in-the-javascript-language-2b0f24d57397)
