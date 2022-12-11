*Inspection* and *reflection* refer, collectively, to the various ways in which you can get Ruby objects to tell you about themselves during their lifetimes.

`"".methods` **All the methods** that the receiver responds to. It includes *singleton* methods as well as any methods it can call by the inclusion of one or more *modules* or inherited *classes* anywhere in its *ancestry*.

`String.instance_methods` *All the instance methods* that *instances* of `String` are endowed with. In this case it's the same number of methods as `"".methods`.

`String.instance_methods(false)` Only instance methods defined *directly on* `String`.

