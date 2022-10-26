- *Class variables* are *inherited* PLUS it is *accessible* in instance methods.
- *Class instance variables* are NOT inherited PLUS it is NOT *accessible* in instance methods.

```ruby
class Vars

  @class_ins_var = "class instance variable value"  #class instance variable
  @@class_var = "class variable value" #class  variable

  def self.class_method
    puts @class_ins_var
    puts @@class_var
  end

  def instance_method
    puts @class_ins_var
    puts @@class_var
  end
end

Vars.class_method

puts "see the difference"

obj = Vars.new

obj.instance_method

class VarsChild < Vars
end

VarsChild.class_method
```
