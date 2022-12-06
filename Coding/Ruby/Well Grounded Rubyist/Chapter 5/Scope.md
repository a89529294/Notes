**Scope** refers to the reach or *visibility* of identifiers, specifically variables and constants.

## global scope & global variables
- *Global scope* covers the the entire program. *Global varaibles* start with `$`.
- *Global variables* never go out of scope.
- Some *built in* global variables:
	- `$0`: the name of the start up file for the currently running program.
	- `$:` or `$LOAD_PATH`: directories that Ruby searches when you load external files.

## local scope & local variables
- At any given moment, your program is in a particular local scope.
- The *top level* (outside of all definition blocks) has its own local scope.
- Every *class* or *module*-definition block has its own local scope.
- Every *method* definition (def) has its own local scope.
- Every crossing of `class`, `module`, `def` creates a new scope and the outer one *cannot* be seen.

## class variables
- *class variables* have a niche to fill: visibility to a class and its instances, and to no one else.
