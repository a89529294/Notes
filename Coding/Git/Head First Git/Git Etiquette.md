- commit *early*, commit *often*
- each commit should correspond to a *functionality*
- Always write *meaningful messages*
	- Use *imperative* mood, i.e. as if you are giving the computer a command. Instead of `updated documentation` use `update ddocumentation`
	- Run `git c` without `-m` so you can use vsc to write longer, more meaningful messages. 
	- Focus on the *why* and *what*, e.g. header contains the *what*, body contains the *why*

## Examples of good commit messages
```txt
feat: update css style names to be consistent

- Ensures camel case styling
- Aligns the names for all css classes to be in line with out spec
```
\*\* Note the use of *imperative* mood in the title/header
\*\* Note the blank line seperating header from body
\*\* header is all lowercase, each line in the body is capitalized 


## Header Types
- `feat` adding features or enhancements
- `fix` bug fixes
- `docs` documentation changes
- `chore` tooling changes


