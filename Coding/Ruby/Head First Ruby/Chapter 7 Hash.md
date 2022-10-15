# Syntax
```ruby
elements = {:H=>"Hydrogen", :Li=>"Lithium"}

elements[:H] # access key/value
elements[:O] = "Oxygen" # add new key/value

elements_simplified = {H:"Hydrogen", Li:"Lithium" } 
# elements_simplified has the same value as elements
```

In Ruby, a **Hash** can use any *object* as *keys* e.g. strings, numbers and symbols.

## Methods on hash objects
```ruby
my_hash = {H:'Hydrogen', O:'Oxygen'}

my_hash.each do |key, value|
	...
end

my_hash.has_key? 'O' # true
my_hash.has_value? 'Lithium' # false

my_hash.keys # [:H,:O]
my_hash.values # ['Hydrogen','Oxygen']
```

## Ways of passing in arguments to a function
- Passing in a *plain hash*
```ruby
def create_user(opts={})
	puts opts[:name], opts[:age], opts[:occupation]
end

create_user({name:'A', age:11, occupation=''})
```
Down side is you can make a *typo* when passing in the hash argument and get *no warning*.

- Using *keyword arguments*
```ruby
def create_user(name:, age:0, occupation:'')
	puts name, age, occupation
end

create_user(name: 'A')
```
Now if you pass in something not listed as a keyword you will get a warning. Note *name* has no default value so it is *required*.

*Note* if you use positional params with keyword arguments,you have to list the keywords *last*.

## Hash default object
```ruby
empty_elements = Hash.new(0) # pass in 0 to use as default object for 
		                     # missing keys
empty_elements[:wut] # 0 instead of nil
```






