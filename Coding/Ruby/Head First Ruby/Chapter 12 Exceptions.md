```ruby
class MyException < StandardError
end

begin 
	raise MyException, 'oops'
rescue MyException => e
	puts e.message
ensure 
	puts 'I will get printed no matter what'
end
```

- `raise` can be called with a *string* or with any class that extends *Exception*. *StandardError* extends *Exception*. 
	- `raise 'oops'` # raises a *RuntimeError*
	- `raise StandardError` 
	- `raise StandardError, 'oops'`
- You can have *more than one* `rescue` clause
- Put the class you want the `rescue` clause to handle right after the keyword, otherwise it will handle *all exceptions*.
- `ensure` runs last no matter what happens.
- `retry` keyword can be added in a `rescue` clause to rerun the code in the surrounding `begin/end` block.