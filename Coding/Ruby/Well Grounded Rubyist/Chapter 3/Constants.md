- The name of every constant *begins with a capital letter*.
- A *constant defined in a class* can be referred to from inside the class’s instance or class methods directly.
- Use `::` to look up constants defined in a class from outside
```ruby
class Ticket
	VENUES: ['Town Hall', 'Convention Center']

	def print_venues
		puts VENUES
	end

	def self.print_venues
		puts VENUES
	end
end

# all the same
Ticket.new.print_venues 
Ticket.print_venues
puts Ticket::VENUES
```