There are three flavors of block varaibles
1. Local variables that exist already when the block is created. 
2. Block parameters, which are always block-local.
3. Variables defined in block parameters after `;` These aren’t assigned to but do protect any same-named variables from the outer scope

```ruby
a = 1
b = 2
1.times do |idx; a|
	a = 10
	b = 20 
	c = 999
end

puts a, b # 1, 20
puts c # error, cannot find c
```
