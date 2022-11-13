# RubyGems
- **RubyGems**, often just called **Gems**, are packages of code that you can download, install, and use in your Ruby programs or from the command line.
- [RubyGems](https://rubygems.org/)

## $LOAD_PATH
- In `irb` you can check the `$LOAD_PATH` to understand where *Ruby* looks for code.
- By using `requrie 'rails'` what you are doing is putting *rails* lib directory onto `$LOAD_PATH`.
- The `lib` directory in each *Gem* is the most important. When you `require 'freewill'`, *Ruby* loads `freewill.rb` from the `lib` directory.

## A few gem commands
- `gem list` shows all the installed gems.
- `gem list | grep 'rails'` to filter displayed gems.
- `gem env` prints out some metadata. 
	- In particular it shows where all the gems are installed for the current *Ruby* version under `INSTALLATION DIRECTORY`.
	- `EXECUTABLE INSTALLATION DIRECTORY` Some Gems provide commands that you can use directly from a terminal prompt.


## Debugging
- Put the following right after you `require` a *Gem*, it will print out the full path to the loaded file. In this example we are requiring the freewill *Gem*.
```ruby
puts $LOADED_FEATURES.grep(/freewill\.rb/)
```