- *Unique* and *immutable*
```ruby
:abc.object_id == :abc.object_id # true, uniqueness of symbol :abc
# there is no way to mutate a symbol

'abc'.object_id == 'abc'.object_id # false
```
- Usually used as *method arguments* and *hash keys*
```ruby
def MyClass
	attr_accessor :name
end
obj.send(:my_method)

{:first_name => 'Albert'} # is the same as writing
{first_name: 'Albert'} 
```