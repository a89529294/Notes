Basics
```ruby
begin
	100/0
rescue 	
	puts 'Something bad happened'
end
```
Handling *specifc exception* and assigning it to a variable
```ruby
begin
	100/0
rescue ZeroDivisionError => e
	p e
end
```
In a method or code block, you can just use `rescue` by itself. This will handle every exception in the method/block.
```ruby
def method_one
	puts 'hi'
	100/0
	rescue
		puts 'Something bad happened.'
end
```
You can also re-raise exceptions, the second `raise` will simply raise whatever was caught.
```ruby
begin
	100/0
raise
	puts "No!"
	raise
end
```
`ensure` guarantees code within it will run no matter what
```ruby
begin
	100/0
rescue
	puts "You will see this only if there is an exception."
ensure
	puts "You will see this no matter what!"
end
```