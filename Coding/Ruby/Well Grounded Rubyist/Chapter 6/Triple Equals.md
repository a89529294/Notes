- Also called the *Case equality operator*, *membership operator*.
- `a === b` check if `b` is a *member* of `a`.
```ruby
(1..10) === 1 # true
(1..10).include? 1 # true

String === 'foo' # true
'foo'.is_a? String # true
```