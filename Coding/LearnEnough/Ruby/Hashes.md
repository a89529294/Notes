# What is a Ruby hash?
You can think of a *Ruby hash* as comparable to *JavaScript object*.

```Ruby
# using strigns as keys
user = {}
user['first_name'] = 'Albert'
user['last_name'] = 'Chang'

# using symbols as keys
user = {}
user[:first_name] = 'Albert'
user[:last_name] = 'Chang'

# initializing hash with some key value pairs
# using strings as keys
user = {'first_name'=>'Albert', 'last_name'=>'Chang'}
# using symbols as keys (the following are equivalent)
user = {:first_name=>'Albert', :last_name=>'Chang'}
user = {first_name:'Albert', last_name:'Chang'}

# retrieving values
user['first_name']
user[:first_name]
```