- Typical *class* consists of a *collection of method* definitions. Classes usually exist for the purpose of being instantiated.
- *Instance variables* enables individual objects to remember state
	- instance variable names always start with a single `@`
	- instance variables are only *visible* to the object to which they *belong*
	- an instance variable *initialized in one method* inside a class can be used by any instance method defined within that class
- *Setter* method syntactic sugar
```ruby
class Ticket
	def price=(price)
		@price = price
	end
end

ticket = Ticket.new
# The following are the same, interpreter ignores empty space before =,
# in both cases you are calling the price= method
ticket.price= 55.0
ticket.price = 55.0
```
- *Class methods* and *instance methods* aren’t radically different from each other; they’re all methods, and their execution is always triggered by sending a message to an object. It’s just that the object getting the message may be a class object.
- Method Notation
	- `Ticket#price` refers to instance method `price` in class `Ticket`
	- `Ticket.most_expensive` refers to class method `most_expensive` in class `Ticket`
	- `Ticket::most_expensive` same as above