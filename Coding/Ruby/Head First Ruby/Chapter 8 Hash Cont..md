# Invoking hash.new
- Passing in an *argument*
```ruby
bodies = Hash.new(CelestialBody.new)
```
- Passing in a *block*
```ruby
bodies = Hash.new do |hash, key|
	body = CelestialBody.new
	hash[key] = body
end

# assuming CelestialBody has name attribute
bodies['Earth'].name = 'Earth' 
# Since 'Earth' is a new key the return value of the block
# is used here, then subsequently mutated by assigning a 
# value for its name attribute
```
Two things happen in the block
1. Assigned a new `body` to `hash[key]`
2. Returned the new `body` to use as the value for `hash[key`

One more thing, just like passing in argument(the argument will be used only when accessing a new key), the *block only runs when you are accessing a new key*.
## When to use which
1. Only pass in *object* directly *IF* it is immutable, e.g. *number*.
2. Otherwise use a *block*

