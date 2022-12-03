- the `Class` class is a *subclass* of the `Module` class, so every class object is also a module object.
- The main differences are
	- *Classes* can be instantiated; *modules* cannot.
	- *Classes* can only have one *super class*, but it can have multiple *modules* mixed in.
```ruby
module MyFirstModule
	def ruby_version
		system("ruby -v")
	end
end
```
- Where Ruby looks for methods for an object `obj` (assuming modules are mixed in using `include`, flip order of class & module when using `prepend`)
	- `obj` itself
	- Modules *prepended* to its class, in reverse order of prepending (bottom to top)
	- Its *class*
	- Modules *included* in its class, in reverse order of inclusion (bottom to top)
	- Modules *prepended* to its *superclass*
	- Its class’s *superclass*
	- Modules *included* in its *superclass*
	- and so on, untill we reach `kernel` module which is mixed in to `Object` or `BasicObject` class.
	- If there are multiple methods with the same name in a class or in the modules included in a class, method search is from bottom of the file and up.
- There is a third way of incorporating *modules* into classes, `extend`. Use it just as you would use `include`, and `prepend`.
	- The extended module's methods become *class methods*.
	- The extended module *does not* show up in the *ancestor chain*.
```ruby
module T
end

module Z
end

class A
	extend T
	include Z
end

A.ancestors = [A, Z, Object, Kernel, BasicObject]
```
