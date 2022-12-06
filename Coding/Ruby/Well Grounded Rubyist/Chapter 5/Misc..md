- *constant lookup* is similar to file look up in that there is *relative* and *absolute* paths.
- You can denote an *absolute* path by starting with `::`
- If Ruby cannot find a *constant* it will look up a level until it finds the constant or throws an error. This is not the case with *local variables*.
```ruby
module M 
	class C 
		class D
			Y = 2	
	        module N
				X=1 
				puts Y #2
			end
		end 
		puts D::N::X #1
		puts ::M::C::D::N::X #1
	end
end
puts M::C::D::N::X #1
```