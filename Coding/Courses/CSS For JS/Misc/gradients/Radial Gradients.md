*Radial gradients* emerge from a single point and smoothly spread outward in a circular or elliptical shape.

When creating a radial gradient, you indicate the *center of the gradient*, as well as the *size and shape of the ending shape*. You also provide a list of color stops, starting from the center and progressing out. Color stops specify which colors go where in the gradient.

## syntax
`background-image: radial-gradient(shape size at position, color1, color2, ...)`
- **shape**: either `circle` or `eclipse`, **eclipse being the default**.
- **size**: describes the size of the gradient ending shape. It can be given *explicitly* or by *keyword*. 
	- Valid *keyword* is one of the following:
		1. *closest-side*: to size a gradient such that it meets the closest side to its center
		2. *closest-corner*: the gradient meets the closest corner
		3. *farthest-side*: the gradient meets the farthest-side
		4. **farthest-corner(default value)**: the gradient is sized in a way that it meets the farthest-corner
	- Otherwize, we can define the size *explicitly*:
		1. `circle 30px` You can only specify one value in absolute unit.
		2. `ellipse 20% 30%` You have to specify two values, in either percentages or absolute units.
		3. When the `<ending-shape>` keyword is omitted, the gradient shape is determined by the size given. One `<length>` value provides a circle, while two values in `<length-percentage>`units provide an ellipse.
		4. the length/percentages above denote the circle/ellipse *radius*.
- **position**: where to place the *center of the gradient*. **Defaults to `center`**, which means put the center of the gradient at the center of the element. [[<position> css data type]].
```css
.class1 {
	 background: radial-gradient(ellipse 20% 20px at 50% 50%, #ff0000, #0000ff);
}

.class2 {
 background: radial-gradient(circle 50px at 50% 50%, #ff0000, #0000ff);
}
```