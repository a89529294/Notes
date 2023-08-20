1. `nano my_script.sh`
2. add `#! /bin/zsh` as the first line
3. add the following as an example
```zsh
echo "Hello!, the current date and time is:"
date
echo "And the current directory is:"
pwd
```
4. `ctrl O`, then press `enter` to save file.
5. `chmod u+x my_script.sh` to make it executable
6. `./my_script.sh` to run it.

## Variables in scripts
`city=London` make sure there is no space surrounding `=`
In order to read the variable, add `$` in front of it.
`echo "Welcome to $city"` 

## Turn cmd line arguments to variables
When you enter a script name followed by a space and one or more terms, each term is automatically assigned to variables called $1, $2, $3, and so on.

## Get interactive user input
`read name_of_variable`
```zsh
#!/bin/zsh
echo "What do you have to say for yourself?"
read reply
echo "Oh yeah? Well, $reply to you too!”

```

## Put the output of a cmd into a variable
- `today=$(date)`
- `directory=$(pwd)`

## Control flow
```zsh
if [ condition to test ]; then
	action to take
elif [ condition to test ]; then
	action to take
else
	action to take
fi
```
- starting and ending spaces in square brackets are mandatory.
- `then` must be either on a line by itself, or on the same line as `if` after a semicolon.

## Loops
_while_
```zsh
#! /bin/zsh

count=1
while [ $count -le 10 ]
do
	echo $count
	((count++))
done
```
- (()) means this is a mathematically expression.

_for_
```zsh
#! /bin/zsh

for i in 1 2 3 4 5
do
	echo "this is iteration $i"
done
```

## Math
`((7*5+3))` calculate 
`number=$((7*5+3))` assign result to variable
`let "number=7*5+3"` same as above



