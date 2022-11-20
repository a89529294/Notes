## load
- `load 'file_name.rb'` looks in *current dir* then *$LOAD_PATH*
- `load 'path_to_file.rb'` looks for file according to path
- You can even wrap a `load` call in a *conditional statement*, in which case the call will be executed only if the condition is true.
- A call to load *always loads* the file you ask for, whether you’ve loaded it already or not.

## require
- `require 'file_name'` looks for file in *$LOAD_PATH*
- `require 'path_to_file'` looks for file according to path
- Does not reload the same file if called a second time.
- No need for `.rb` extension.

## require_relative
- `require_relative 'file_name'` looks for file in *current dir*.
- `require_relative 'path_to_file'` looks for file according to path.
- No need for `.rb` extension.