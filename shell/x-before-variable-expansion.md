# x before variable expansion in old code

```bash
[ x"$foo" = xbar ] 
```

Some scripts are written to be be compatible with older versions of shell that lack the `[[` command. They use this (clever but unreadable) hack.

```bash
[[ $foo = bar ]] 
```
