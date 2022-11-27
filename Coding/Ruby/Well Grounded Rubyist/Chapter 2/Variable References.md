For the most part, *variables* hold **references** to objects, not the objects themselves.

Unless the objects are *numbers*, *false*, *true*, *nil*, and *symbols*. In such cases the objects are stored in variables as **immediate values**. You can think of the variables holding the values themselves rather then references.

One consequence of variables holding immediate values is that those objects are **unique**. There is only one `1`, `false`, `:my_symbol` in every program.

```ruby
1.object_id == 1.object_id      #true
'1'.object_id != '1'.object_id  #true 
```
