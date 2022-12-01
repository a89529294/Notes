- *Classes* are **objects**! The only kind of object that can spawn other objects.
- Every class, `Object`,`Person`,`Ticket` is an instance of a class called `Class`.
- Like other objects, *classes* can be created. Following are some ways to create classes. 
Using `class` keyword
```ruby
class Ticket
	def speak
		puts "hi there"
	end
end

Ticket.new.speak # "hi there"
```
Using `new` keyword
```ruby
Ticket = Class.new do
	def speak
		puts "hi there"
	end
end

Ticket.new.speak # "hi there"
```