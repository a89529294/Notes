- `dup` & `clone` both produces shallow copies of an object.
	- on *fronzen* objects, *dup* will give you an *unfronzen* object whereas *clone* gives you a *frozen* object.
	- When using [`dup`](https://ruby-doc.org/core-3.1.2/Object.html#method-i-dup), any modules that the object has been extended with will not be copied.
- `freeze`ing and object prevents you from modifying it. 
```ruby
str = 'hello'.freeze
str.replace('goodbye') # error

str = 'goodbye' # all good, since we are reassigning, not modifying

arr = ['1','2','3'].freeze # we are freezing the references the array is holding. [location#1, location#2, location#3] we can only change what the locations are holding not the locations themselves.
arr[0] = '5' # error, attempting to do this [location#4, location#2, location#3]. i.e. assigning a new location to array index 0.
arr[0].replace('5') # all good since the array still looks like 
# [location#1, location#2, location#3]
```