- Must be *capitalized*.
- Ruby classes are *constants*
- *Constants* can be reassigned so it's best to use `.freeze` on a constant.
- By convention, our own *constants* should be in *ALLCAPS*.
- *Constants* cannot be used within methods.

```ruby
class Tester
	ITEMS = [1,2,3].freeze

	def print 
		p ITEMS
	end
end

p Tester::ITEMS
```
- Note that to *access constants within the class* just use the constant name; Accessing constants outside the class use `ClassName::CONSTANTNAME`
- 