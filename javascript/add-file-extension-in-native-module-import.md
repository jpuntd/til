# Include file extension when importing native JavaScript modules.

Always use imports including file extensions.

Don’t

    import './my-todo-list/MyTodoList.component';

Do

    import './my-todo-list/MyTodoList.component.js';

Sometimes an IDE will generate import statements without the file extension. Or it omits the last part (eg if the file is named index.js). This will work when using module loaders because they look up the file extension but it won’t work with ES modules in the browser.

Make sure the module files are served with a `Content-Type` header that contains a JavaScript MIME type such as `text/javascript`.

Otherwise you'll get a strict MIME type checking error along the lines of "The server responded with a non-JavaScript MIME type" and the browser won't run your JavaScript.

[source](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)
