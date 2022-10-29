```ruby
require 'ostruct'

hash = { name: "Jeremy Walker", age: 21, location: "Nomadic" }
person = OpenStruct.new(hash)

# Now you can read and write using dot notation
person.name 
person.age = 35
```

```ruby
# The following are the same, note person is of type OpenStruct
people.sum { |person| person.age } people.sum(&:age)
```