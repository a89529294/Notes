- **Class variables** provide a storage mechanism that’s shared between a class and instances of that class, and that’s not visible to any other objects.
- `@@my_store`
- *Class variables* are shared downwards across hiearchy, so class variables defined in *parent* class can be accessed in *child* class.
```ruby
class Parent
	@@values = 100
end
class Child < Parent
	@@values = 200
end
class Parent
	puts @@values # 200
end
```