## Blocks
A block is a chunk of code that you associate with a method call. While the method runs, it can invoke (execute) the block one or more times.

- You can only pass in one block to a method. (unless you use *procs*)
- You cannot create a block on its own and use it across many methods, it it tied to a method call. (unless you use *procs*)
- Block HAS to be defined as the last parameter. (but most of the time we don't explicitly set it)

1. *Explicitly* passing in the block, note the `&` 
```ruby
def f(&my_block)
	puts 'Start of method'
	my_block.call
	puts 'End of method'
end

f do
	puts 'In the block!'
end

# 'Start of method'
# 'In the block!'
# 'End of method'
```

2. Conventional way
```ruby
def f
	puts 'Start of method'
	yield
	puts 'End of method'
end

f do
	puts 'In the block!'
end

# 'Start of method'
# 'In the block!'
# 'End of method'
```

3. Passing in arguments to the *method*
```ruby
def f (arg)
	puts "Start of #{arg}"
	yield
	puts "End of #{arg}"
end

f 'method' do
	puts 'In the block!'
end

# 'Start of method'
# 'In the block!'
# 'End of method'
```

4. Passing in arguments to the *block*
```ruby
def f
	puts "Start of method"
	yield 'block'
	puts "End of method"
end

f do |arg|
	puts "In the #{arg}!"
end
```

5. `{}` syntax instead of `do...end`
```ruby
def f
	puts 'Start of method'
	yield 'block'
	puts 'End of method'
end

f {|arg| puts "In the #{arg}!"}
```