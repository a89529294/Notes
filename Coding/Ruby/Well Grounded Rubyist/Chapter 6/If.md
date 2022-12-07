- The following are the same
```ruby
if x = 5
	puts 'x == 5'
end

if x = 5 then puts 'x == 5' end

puts 'x == 5' if x = 5
```
- Value of an `if` statement
	- If an `if` statement succeeds, the entire statement *evaluates* to whatever is represented by the code in the *successful branch*.
	- An `if` statement that doesn’t succeed anywhere returns `nil`
```ruby
x = 0 

res = if x < 0
	'negative'
elsif x > 0
	'positive'
else
	'zero'
end

puts res # 'zero'
```

## Pitfalls
- `if` does *NOT* have its own scope, only `class`,`module`,`def`,`proc`,`block` have their own scopes.
- Ruby, like JS, scans and initialize *local variables* before executing code.
```ruby
if false
	x = 1
end

puts x # nil
puts y # raises an Error
```