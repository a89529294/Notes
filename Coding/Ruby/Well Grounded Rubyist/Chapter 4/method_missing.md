```ruby
class Person
	PEOPLE = []
	attr_reader :name, :hobbies, :friends

	def initialize(name)
		@name = name
		@hobbies = []	
		@friends = []
		PEOPLE << self
	end

	def has_hobby(hobby)
		hobbies << hobby
	end

	def has_friend(friend)
		friends << friend
	end

	def self.method_missing(m, *args)
		m_str = m.to_s
		attr = m_str[9..-1]
		if m_str.start_with?('all_with_')
			if public_method_defined?(attr)
				PEOPLE.filter { _1.send(attr).include? args[0] }
			else
				raise ArgumentError, "Can't find #{attr}"
			end
		else
			super
		end
	end
end

j = Person.new('John')
p = Person.new('Paul')
g = Person.new('George')
r = Person.new('Ringo')

j.has_friend(p)
j.has_friend(g)
g.has_friend(p)
r.has_hobby('rings')

Person.all_with_friends(p).each do |person|
	puts "#{person.name} is friends with #{p.name}."
end

Person.all_with_hobbies('rings').each do |person|
	puts "#{person.name} is into rings."
end
```