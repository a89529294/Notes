- *index access*
```ruby
a = ["Panama", "a canal", "a plan", "A man"]
a[-1] # "A man"
a[a.length - 1] # "A man"
a.last "A man"
```

- *slicing*
```ruby
alphabets = ('a'..'b').to_a
alphabets.slice 3 # returns the element at index 3
alphabets[3] # same as above

alphabets.slice 5, 2 # returns the elements from 5 for 2 lengths
alphabets[5, 2] # same as above

alphabets.slice 1..3 # returns the elements from 1 to 3 inclusive
alphabets[1..3] # same as above
```

- *sort* & *reverse*
```ruby
arr = [42, 8, 17, 99]

arr.sort # returns a new array [8, 17, 42, 99]
arr.sort! # mutates arr

arr.reverse # returns a new array with elements reversed
arr.reverse! # reverses arr in place
```

- *push*, *pop* & *unshift*, *shift*
```ruby
arr = [1, 2, 3, 4]

arr.push 5 # mutates arr by adding 5 to the end
arr.pop # mutates arr by removing end element

arr.unshift 5 # mutates arr by adding 5 to the start
arr.shift # mutates arr by removing first element

arr << 5 # mutates arr by adding 5 to the end (shovel operator)
```

- *looping*
```ruby
arr = [1, 2, 3, 4]

for i in 0..arr.length-1 do
	puts arr[i]
end

# above and below are equivalent

arr.each do |v|
	puts v
end
```