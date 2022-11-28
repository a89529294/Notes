- You can teach *methods* to *objects* directly, these methods are called *singleton* methods.
```ruby
obj = Object.new
def obj.talk
  puts "I'm a talking object."
end

obj.talk # "I'm a talking object."
```
- Some important methods on almost every *Ruby object*
```ruby
obj = Object.new

obj.object_id #283120
obj.respond_to? 'object_id' # true
obj.send('object_id') # 283120
```
- Rules for *parameters*
	- All the *optional* ones have to occur in the middle. (`*args` and `a=z`). Note that there maybe no left or right sides.
	- *Required* ones have to be on the left or right or both.
	- `*args` cannot be on the left of default arguments `a=1`
	- Following is all the valid arrangements.
```
R => required, S => sponge(*args), D => default argument(a=1)
R
S
D
R S
S R
R D
D R
D S
R D S
R D S R
```
- When *Ruby* sees a plain word like `s`, `ticket`, `puts`, `def` or `user_name`, it interprets it as one of three things
	1. local variable
	2. keyword
	3. method call