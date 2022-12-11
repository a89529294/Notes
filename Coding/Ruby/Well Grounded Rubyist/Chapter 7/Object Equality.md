The `Object` class defines three equality-test methods: `==`, `eql?`, `equal?`.

At the `Object` level, all equality-test methods do the same thing: they tell you whether two objects are exactly the same object. i.e. whether they have the same *object_id*.

Further down the road, in *classes other than Object*, `==` and/or `eql?` are typically redefined to do meaningful work for different objects.

```ruby
str1 = 'text'
str2 = 'text'

# content equality
str1 == str2 # true
str1.eql? str2 # true

# memory location equality
str1.equal? str2 # false
```