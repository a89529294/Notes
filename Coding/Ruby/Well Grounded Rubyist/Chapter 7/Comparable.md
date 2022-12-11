If you want your objects to be *comparable* with each other
1. Mix in `Comparable` modules
2. Define `<=>` as an instance method in the class

```ruby
class MyClass
	include Comparable
	def <=>(b)
		if (...) # a less than b
			return -1
		elsif (...) # a equal to b
			return 0
		else # a greater than b
			return 1
		end
	end
end
```

Now you get a suit of comparison methods: `==`, `!=`, `>`, `<`, `>=`, `<=`, `between?`.