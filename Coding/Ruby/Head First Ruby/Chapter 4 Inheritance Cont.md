## The `initialize` method
The new method is needed to actually create the object; initialize just sets up the new object’s instance variables.

```ruby 
class Animal
	attr_accessor :type, :name

	def initialize(type,name)
		@type = type
		@name = name
	end
end

gorilla = Animal.new('gorilla','Frank')
# creates a new animal instance and immediately invoke the 
# initialize method on the newly created instance passing in
# the arguments of new to initialize
```

## self
In *instance methods* `self` refers to the object the instance method is invoked on 

```ruby
class Animal
	attr_accessor :name

	def print_name
		puts "The animal is #{self.name}."
	end
end

dog = Animal.new
dog.name = 'Dobby'
dog.print_name # The animal is Dobby.
```

Often times you can leave `self` off so line 7 in above code is equivalent to `puts "The animal is #{name}."`

One situation where you *CANNOT* leave `self` off is when you want to use the *writer method* of an instance variable.

```ruby
class Animal
	attr_accessor :name

	def modify_name(name)
		self.name = name 
		# name = name  won't work
	end
end
```

`name = name` won't work since Ruby will think this is just an ordinary assignment. 

Remember that `attr_accessor :name` is just shorthand for 
```ruby
def name=(name) 
	@name = name
end

def name
	@name
end
```

In *Class* definition but outside of *instance methods* `self` refers to the Class itself.

```ruby
class Animal
	def self.talk
		puts "hi"
	end
end

Animal.talk
```


