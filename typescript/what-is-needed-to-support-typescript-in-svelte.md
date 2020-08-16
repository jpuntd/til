# How is TypeScript support for Svelte handled?

To support TypeScript in Svelte two things are needed.

## support for tsc, the TypeScript compiler: svelte-preprocess

Svelte has its own compiler. The Svelte compiler support for TypeScript is handled by **svelte-preprocess**. It passes `<script lang="ts">` blocks through tsc for transpiling, but will not typecheck them.

## introspection for editors via the Language Server Protocol standard: svelte-language-server

TypeScript's TSServer is a node API that responds to requests from text editors via the [Language Server Protocol standard](https://microsoft.github.io/language-server-protocol/overviews/lsp/overview/). Svelte has **svelte-language-server** that is used by for instance a VS Code extension.
