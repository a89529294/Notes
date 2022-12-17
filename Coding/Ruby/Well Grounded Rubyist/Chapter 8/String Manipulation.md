*Reading*
```ruby
string = 'Ruby is a cool language'
string[5] # 'i'
string[5,2] # is, from index 5 count 2
string[5..6] # is, from index 5 to 6, inclusive
string[0..-1] # 'Ruby is a cool language'
string['is'] # 'is'
string[/\w/] # 'R'

# you can also use slice instead of []
string.slice(0..-1) # 'Ruby is a cool language' 
```
*Writing* Note we are *mutating* the original string
```ruby
string = 'Ruby is a cool language'
string['cool'] = 'great'
string # 'Ruby is a great language' 
string[-9..-1] = "thing to learn!"
string # "Ruby is a great thing to learn!"
```
*Combining*
```ruby
str = "Hi "
str + "there." # returns "Hi there."
str # still "Hi "

str1 = "Hi "
str1 << "there." # returns str1, which is mutated to "Hi there."
```
*String Interpolation*
- Ruby called `to_s` on whatever is inbetween `{..}` in a double quoted string.
*Querying Strings*
```ruby
str = "Ruby is a cool language."
str.include?("Ruby") # true, can only pass in strings
str.start_with?(/[A-Z]/) # true, can pass in string or regex
str.empty? # false, same as str.length == 0
```
*String Comparison*
```ruby
'a' > 'b' # false
'a' > 'A' # true

'a'.ord # 97
'b'.ord # 98
'A'.ord # 65
```
*String transformations*
```ruby
string = "David A. Black"
string.rjust(20) # "      David A. Black"
string.ljust(20) # "David A. Black      "
string.center(20)# "   David A. Black   "
string.center(20,'-') # "---David A. Black---"

string.chop # "David A. Blac"
string.chomp # "David A. Black", does nothing because chomp by default only removes \n
string.chomp('ck') # 'David A. Bla'

string.clear # "", note this is a mutation
string.swap("(to be named later)") # "(to be named later)", this a a mutation
```
*String/Number base conversion*
```ruby
'a'.to_i(16) # 10, convert receiver to base 10 number from base 16
10.to_s(16) # 'a', convert receiver to base 16 from base 10
```