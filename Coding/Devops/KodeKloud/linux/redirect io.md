## redirect stdout
```bash
echo $SHELL > shell.txt # replaces

echo $SHELL >> shell.txt # appends
```

## redirect stderr
```bash
cat missing_file 2> error.txt

cat missing_file 2>> error.txt

cat missing_file 2> /dev/null # if we do not want errors to show up at all
```