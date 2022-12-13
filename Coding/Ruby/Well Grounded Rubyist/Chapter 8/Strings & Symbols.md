They provide all the functionality of *text* representation and manipulation.

- `%Q[]` interpolated string, `$q[]` non-interpolated string except for `[`,`]`,`\`
- You can use different delimiters, `%Q{}` or `%Q()`
- `%Q[]` is the same as `%[]`
```ruby
x = 'hi'
p %Q[#{x} Ram!] # "hi Ram!"
p %q[#{x} Ram!] # "\#{x} Ram!"
p %Q[' " '] # "' \" '"
p %q[' " '] # "' \" '"
```

- multiline strings, `EOM` can be anything, its just a delimiter. The `<<` is called **heredoc**.  
- The ending delimiter must be the only thing on the line it occurs and must be flushed left.
```ruby
text = <<EOM
This is the first line.
This is the second line.
EOM

p text # "This is the first line.\nThis is the second line.\n"
```
- `<<-` removes the requirement that the ending delimiter must be flushed left.
```ruby
text = <<-EOM
This is the first line.
      EOM
```
- `<<~` *squiggly heredoc* strips leading white spaces.
```ruby
class RubyWelcomeWagon
  def message
    <<~EOM
      Welcome to the world of Ruby!
      We're happy you're here!
	EOM 
  end
end
RubyWelcomeWagon.new.message # "Welcome to the world of Ruby!\nWe're happy you're here!\n
```
- By default, *heredoc* produces a double quoted string. To produce a single quoted string enclose the *delimeter* with `''`.
```ruby
text = <<-'EOM'
Single-quoted!
note the literal \n
EOM

puts text 
# Single-quoted!
# Note the literal \n.

```
- The <<EOM (or equivalent) doesn’t have to be the last thing on its line. Wherever it occurs, it serves as a placeholder for the upcoming heredoc.
```ruby
a = <<EOM.to_i * 10
5
EOM
puts a # 50
```
- Whatever is below `<<EOM` and above the closing `EOM` gets placed into `<<EOM`
```ruby
do_something_with_args(a, b, <<EOM)http://some_very_long_url_or_other_text_best_put_on_its_own_line
EOM

# the url gets passed in as an argument to the function
```