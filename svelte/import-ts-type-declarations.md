# import TypeScript type declarations in Svelte

To import a type or interface use TypeScript's type modifier...

import type { SomeInterface } from './SomeFile';

... because svelte-preprocess doesn't know whether an import is a type or a value. It only transpiles one file at a time without knowledge of the other files and therefore can't safely erase imports which only contain types without this modifier present.

[source](https://github.com/sveltejs/svelte/blob/master/site/content/faq/500-what-about-typescript-support.md)
