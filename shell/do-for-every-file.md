# Perform an action on every file

```sh
# POSIX
for file in ./*.mp3; do
    [ -e "$file" ] || continue
    some command "$file"
done
```

but this doesn't work recursively

```bash
find . -type f -name '*.mp3' -exec some command {} \;
```

Or, if the command accepts multiple input filenames:

```bash
find . -type f -name '*.mp3' -exec some command {} +
```

```bash
# option only for bash 4.0
shopt -s globstar 
for file in ./**/*.mp3; do
  some command "$file"
done
```

Notice that the filenames always include a path. This is to ensure that we never glob a filename that includes a dash because the shell would pass those as an option to our command.
