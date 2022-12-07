```ruby
case answer
when 1
	puts 'the answer is 1'
when 2, 3 then puts 'the answer might be 2'
else
	puts 'idk'
end
```
- What is happening in the background is `1 === answer` is being checked when you see `when 1`. 
- This means you can override `===` if you are using custom objects in `when` like so
  `when custom_obj`.
- At *most* one branch can win.

```ruby
case
when age < 18
	puts "You are not an adult."
when age < 65
	"You cannot retire yet."
else
	"Watch some TV."
end
```
- Pretty much the same as `if`.