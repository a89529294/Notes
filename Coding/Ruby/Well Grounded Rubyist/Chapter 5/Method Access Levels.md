public, protected, private

## private
- *Cannot be sent to an explicit reciever*. In other words, private methods will always be sent to `self`.
- Since it will always be implicitly sent to `self`, you can only invoke private methods where `self` responds to them.
- The only exception is when it comes to *private setters*, you have to specify `self` otherwise Ruby will think you are assigning to a local varaible.

## protected
- Almost like *private*, but In some situations, you can explicitly specify a receiver for a protected method call.
- you can call a protected method on an object x, as long as the default object `self` is an instance of the same class as x or of an ancestor or descendant class of x’s class. 