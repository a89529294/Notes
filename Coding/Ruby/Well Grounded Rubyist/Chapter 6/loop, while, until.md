`loop` The following two loops are equivalent 
```ruby
n = 1
loop { puts n; n+=1; break if n > 3 }

y = 1
loop do
	puts y
	y +=1
	break if y > 3
end
```

`while` The following are the same
```ruby
a = 1
while a < 5
	puts a 
	a += 1
end

b = 1
begin 
	puts b
	b += 1
end while b < 5
```

`until` The following are the same
```ruby
a = 1
until a == 5
	puts a
	a += 1
end

b = 1
begin 
	puts b
	b += 1
end until b == 5
```