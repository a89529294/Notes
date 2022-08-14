## grid-template-areas
- Defined on **grid containers**
```css
.grid-container{
	display:grid;
	grid-template-columns:10rem 1fr 15rem;
	grid-template-rows:5rem 1fr 3rem;
	height:100vh;
	grid-template-areas:
		"header header  header"
		"menu   content ."
		"footer footer  footer"
}
```
- the `.` here refers an area with *no name*.
- the `header header header` refers to a single area *header* that spans three columns.
- By *naming areas*, you are also automatically *naming the lines* surrounding the areas. Assuming the area is ***foo***
	- The name of the area’s starting row line and starting column line will be **_foo_-start**
	- The name of the area’s ending row line and ending column line will be **_foo_end**

## grid-area
- Defined on **grid items**
```css
.header {
	grid-area: header;
}
```
- The above is equivalent to 
```css
.header {
	grid-column: header;  
	/* grid-column: header-start / header-end*/
	grid-row: header;
}
```
- Which is equivalent to
```css
.header {
	grid-column-start: header-start;
	grid-column-end: header-end;
	grid-row-start: header-start;
	grid-row-end: header-end;
}
```
