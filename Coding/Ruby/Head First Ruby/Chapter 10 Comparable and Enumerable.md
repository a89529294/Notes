## Comparable
- A mixin
- To use the *Comparable* mixin 
	1. `include Comparable` in your class
	2. Implement the `<=>` instance method in your class. Return *-1* if a is less than b; return *0* if a is equal to b; return *1* is a is greater than b.
```ruby
class Steak
	attr_accessor :grade
	GRADE_SCORES = {'Prime':3,'Choice':2,'Select:1'}

	def <=>(other)
		GRADE_SCORES[grade] - GRADE_SCORES[other.grade]
end

a = Steak.new
b = Steak.new

a.grade = 'Prime'
b.grade = 'Choice'

puts a > b #true
```

## Enumerable
- A mixin
- To use the *Enumerable* mixin
	1. `include Enumerable` in your class
	2. Implement the `each` instance method. We want to iterate through each item in the collection while passing in each item to the `&block` received by `each`.
```ruby
class WordSplitter  
  attr_accessor :string  
  
  include Enumerable  
  
  def each(&block)  
    string.split(' ').each(&block)  
  end  
end
```

### Constants
- Must be *capitalized*
- Convention is to uppercase every letter `MY_CONSTANT = {name:'A', last_name:'C'}`
- Ruby will use the same reference instead of recreating the object.

