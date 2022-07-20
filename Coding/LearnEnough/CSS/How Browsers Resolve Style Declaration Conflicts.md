An element can have one *id* and multiple *classes* on it. The browser will then go through all the style sheets and gather up all the *declarations* applicable to the element. Merging the declarations in the process. If there are multiple *delcarions* with the same *property* `background-color:red`, `background-color:blue`; The browser will use **order** and **specificity** to determin which *declaration* wins.

```html
	<style>
		#id{
			background-color:grey;
		}
		.alert{
			background-color:red;
			color:blue;
		}
		.success{
			color:black;
			border:1px solid green;
		}
	</style>
	<div id='main' class='alert success'></div>
```

In the above example, the final style object that gets applied to the *div* is
```css
	background-color:grey;
	color:black;
	border:1px solid green;
```

- `background-color:grey` wins because it has the highest *specificity*
- `color:black` wins because it's declared later in the stylesheet (*order*)
- `border:1px solid green` wins because it is the only declaration with that property