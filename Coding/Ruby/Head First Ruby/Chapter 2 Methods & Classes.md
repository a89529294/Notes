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
Notice the special ending `=` for the *writer* method. This allows to use assignment when updating a dog instance's name.
```ruby
dog = Dog.new
dog.name = 'Dobby'
# this is the same as dog.name='Dobby'
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

### Misc.
In Ruby, *classes* are also *objects*! If you put an instance variable outside of instance methods you are creating an instance variable ON the class object itself!.
