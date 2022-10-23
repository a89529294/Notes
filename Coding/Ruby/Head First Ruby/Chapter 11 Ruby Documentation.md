- Ruby's *core classes & modules* are loaded automatically each time Ruby runs.
- The *standard library* is a collection of classes and modules that are distributed with Ruby, but aren’t loaded at startup.
- *instance* methods are denoted with `#`; whereas *class* methods are denoted with `::`
- Watch out for *core* vs *stdlib* classes! You need to `require` stdlib classes. One way to tell is to look at the url of the documentation:
	1. `https://ruby-doc.org/core-2.7.0/Array.html` Note the *core-2.7.0*
	2. `https://ruby-doc.org/stdlib-3.1.2/libdoc/date/rdoc/Date.html` Note the *stdlib-3.1.2* 
