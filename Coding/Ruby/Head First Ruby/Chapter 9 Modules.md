# Syntax
```ruby
module MyModule
	def print_hello
		puts 'hello'
	end
end
```

- You can only put methods in *modules*.
- Must capitalize the module *name*.

## Usage
```ruby
class MyClass
	include MyModule
end
```

- Now `myClass` gains all the methods in `MyModule` as *instance mthods*.

### Misc.
- *Modules* designed to be mixed into *classes* are called *mixins*.
- You can add any number of *mixins* to a class, whereas one class can only inherit from one super class.
- Ruby looks into current class methods first then mixins' methods then super class methods.
- Avoid using `initialize` in *modules*, since if a class that includes the module also has a `initialize` method the one in the *module* WILl NOT get run! `super` does not help since it can only invoke methods in the *super class*.
- `MyClass.ancestors` to get an array of class/mixins that Ruby looks for methods.