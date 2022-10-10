- Ways of loading files in `irb`
	1. cd into the dir the file is in. `irb -I .` then `require 'file_name'`
	2. cd into the dir the file is in. `irb` then 
	`load 'file_name_with_extension'`

## Classes
A *class* is a blueprint for making *objects*.
*Instance variables* are what an object knows about itself.
*Instance methods* are what an object does.

*Instance variables* has to start with `@` 

### Accessor Methods
In Ruby, you cannot access *instance variables* directly outside of the class definition.

You need to defined *accessor* *methods* to access(read, write) *instance variables*. There is nothing special about accessor methods, they are just instance methods!
```ruby
class Dog
	def name=(new_value)
		@name = new_value
	end

	def name 
		@name
	end
```
Notice the special ending `=` for the *writer* method (the `=` is part of the method name!). This allows us to use assignment when updating a dog instance's name.
```ruby
dog = Dog.new
dog.name = 'Dobby'
# this is the same as dog.name=('Dobby')
```

Since it is quite verbose the following is equivalent:
```ruby
class Dog
	attr_accessor :name, :age
end
```

`attr_accessor` creates both the *writrer* and *reader* if we only want one of them we can use
```ruby
attr_writer :name, :age
# or
attr_reader :name, :age
```

### Inheritance
```ruby
class Vehicle 
	attr_accessor :odometer

	def drive
		puts 'the vehicle is moving!'
	end
end

class Car < Vehicle
end
```

Remember that *instance variables* in Ruby do not exist until you write to it.

```ruby
car = Car.new
car.instance_variables #[]
car.odometer = 100
cat.instance_variables #[:@odometer]
```

Almost all *Ruby classes inherit from the Object class* unless we explicitly specify a super class.

```ruby
# The following classes are the same!
class Furniture < Object
end

class Furniture
end
```

### super keyword
```ruby
class Person
	def greet(name)
		puts "hello, #{name}!"
	end
end

class Friend
	def greet(name)
		super
		puts "Nice to see you."
	end
end

friend = Friend.new
friend.greet('Jane')
# Hello, Jane!
# Nice to see you.
```

The `super` references the overriden method. Notice that the argument got passed in implicitly. If you write `super()` then the argument won't get passed in.

### Misc.
In Ruby, *classes* are also *objects*! If you put an instance variable outside of instance methods you are creating an instance variable ON the class object itself!.

Some usefull instance methods on the *Object* class
1. `to_s` converts an object to a string for printing
2. `inspect` converts an object to a debug string
3. `class` tells you which class an object is an instance of
4. `methods` lists the instance methods of an object
5. `instance_variables` lists the instance variables of an object


