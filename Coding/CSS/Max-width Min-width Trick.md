If you want to constrain *min width* to 100px but also prevent *width* from growing to match the container use
```css
.element {
	min-width:100px;
	max-width:max-content;
}
```
This way *element* will grow with its content and be no less then 100px wide