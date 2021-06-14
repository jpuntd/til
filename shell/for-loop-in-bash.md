# for loop in bash

## Bash has arithmetic for loop:

```bash
for ((init; test; next)); do foo; done
```

So counting to 50 goes...

```bash
for ((i = 1;i <= 50;i += 1)); do echo "$i"; done
```

## Brace expansion
Less general solution uses brace expansion.

```bash
for i in 1 2 3 4; do echo "$i"; done
```

So counting to 50 goes...

```bash
for i in {1..50}; do echo "$i"; done
```