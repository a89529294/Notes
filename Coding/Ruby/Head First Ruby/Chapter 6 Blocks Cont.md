You can detect whether a block was passed in to a method usign the `block_given?` method

```ruby
def f
	if block_given?
		yield
	else
		puts 'no block'
	end
end

f { puts 'passed in a block' } # 'passed in a block'
f # 'no block'
```

Just like *methods*, *blocks* return the last expression.

**Do NOT use return in blocks!!**
Within a block body, the return keyword returns from the method where the block is being defined, not the block itself.

```ruby
def print_block_value
	puts yield
end

def other_method
	print_block_value { return 1 + 1 }
end

other_method # Does not print out anything, fix it by simply removing
             # the return
```