- `require` searches for the library in all the defined search paths() and also appends .rb or .so to the file name you enter. It also makes sure that a library is only included once. So if your application requires library A and B and library B requries library A too A would be loaded only once. Use this to import *gems*.
- With `load` you need to add the full name of the library and it gets loaded every time you call `load` - even if it already is in memory.
- `require_relative` should be used for *importing* your own files. This simply means include the file 'relative to the location of the file with the require_relative statement'. You can do the same thing with `require` as well but it is recommended to use `require_relative` for code you wrote.

# Summary
Use `require` to import someone else's code(gems), use `require_relative` to import your own files.
