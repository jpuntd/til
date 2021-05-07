# The bracket [ or double bracket [[ is a command.

That command expects different arguments 
```bash
if [ bar = "$foo" ]; then ...

if [[ bar = "$foo" ]]; then ...
```

```bash
if test bar = "$foo"; then ...
```

But this means also that ...

```bash
[bar="$foo"]     
[ bar="$foo" ]   
[bar = "$foo"]  
[[bar="$foo"]]   
[[ bar="$foo" ]]  
[[bar = "$foo"]]  
```

are wrong. Look.

```bash
testbar="$foo"]     
test bar="$foo" ]   
testbar = "$foo"]  
testbar="$foo"]]   
test bar="$foo" ]]  
testbar = "$foo"]]  
```

