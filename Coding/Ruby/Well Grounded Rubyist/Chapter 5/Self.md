### self
- At every point when your program is running, there’s one and only one `self`.
- What `self` is depends on the *context*
	- top level of program: `main`
	- top level of class definition: the class object itself
	- top level of module definition: the module object itself
	- method definition location 
		- top level: whatever object is `self` when the method is called.
		- in a class: *instance* of the class
		- in a module: *instance* of class that mixed in the module
		- singleton method defined on an object: the object itself.
- *Top level* of a program means outside of any *class*/*module* definition.
- `self` in a method is the *object* to which the message was sent.
- The keywords `class`, `module`, `def` marks a switch to a *new self*.
- For the most part when you call a method with no receiver, `self` is assumed. The one *exception* is when calling methods that end with `=`, e.g. *setter* methods. 
```ruby
class A
	attr_writer :name
	def initialize(new_name)
		name = new_name # this assigns new_name to local variable name
		self.name = new_name # this calls name= with value new_name
	end
end
```
- Every *instance variable* belongs to whatever *object* is playing the role of *self* at the moment the code containing the instance variable is executed.
