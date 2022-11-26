- You can teach *methods* to *objects* directly
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