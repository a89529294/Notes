## Strings
- *Strings* in *Ruby* are **mutable**.
- interpolation in *Ruby*
```ruby
first_name = 'Albert'
last_name = 'Chang'
"#{first_name} #{last_name}" # double quotes are necesary
```
is equivalent to *JavaScript*'s
```js
const first_name = 'Albert'
const last_name = 'Chang'
`${first_name} ${last_name}`
```
- *single* quotes escape everything in it
- By default `split` method splits on *all spaces*
```ruby
"cat   rat\t\tbat\nhat".split # ["cat", "rat", "bat","hat"] 
```


## Equality
Remember everything in *Ruby* is an *object*
- `==` is used to compare the *values* of two objects/variables.
```ruby
a = 'zen'
b = 'zen'
a == b # true
``` 
- `equal?` is used to compare if the operands refer to *the same object*
```ruby
a = 'zen'
b = 'zen'
a.equal? b # false
```

## Falsy values in Ruby
- Only *nil* and *false* are falsy
- `!!false` evaluates to *false*
- `!!nil` evaluates to *false*

