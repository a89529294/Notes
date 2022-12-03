```ruby
class Base
	def report
		puts "'report' method in class Base"
	end
end

class A < Base
end

module M
end

class C < A
	include M
	def report
		puts "'report' method in class C"
		puts 'About to trigger the next higher-up report method...'
		super
		puts "Back from the 'super' call."
	end
end
c = C.new
c.report
```
- In this case `super` finds the next `report` method which is found in `Base`.
- The look up path is C -> M -> A -> Base
- The super *keyword* handles arguments as follows
	- `super` forwards all arguments that were passed to the method from which it is called.
	- `super()` sends nothing to the higher up method.
	- `super(a,b)` sends exactly a, b to the higher up method.
```ruby
class A
	def report; end
end

class B < A
	def report; end
end

b = B.new
p b.method(:report) #<Method: B#report() ...>
p b.method(:report).super_method #<Method: A#report() ...>
```