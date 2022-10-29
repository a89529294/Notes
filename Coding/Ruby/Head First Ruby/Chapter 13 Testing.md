```ruby
require 'minitest/autorun'
require_relative 'path_to_own_file'

class MyTest < Minitest::Test
	def setup
		@my_instance ...
	end

	def teardown
		...
	end

	def test_one
		@my_instance...
	end

	def test_two
		@my_instance...
	end	
end
```

- `setup` runs once before each test method; `teardown` runs once after each test method. There fore you have a *fresh copy* of `@my_instance` for each method!
- Each test methods needs to *start with* `test_`
