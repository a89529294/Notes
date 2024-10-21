## using max-height
```css
.ele {
	max-height:0;
	overflow:hidden;
	transition:all 0.5;		
}

.ele:hover {
	max-height:9999px; //set a number that is guaranteed to be taller than
	                   //actual height
}
```
The reason we are using `max-height` instead of `height` is to animate *height* we need to give specific values, we cannot use keywords like `auto`. But we might not know *height* beforehand so we animate *max-height* instead. 

## using grid
```html
<div class="accordion">
  <div class="accordion-title">Hover me!</div>
  <div class="accordion-body">
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Corporis ullam ipsam dignissimos perspiciatis consequatur itaque maxime nihil cupiditate veniam. Perferendis!</p>
  </div>
</div>
```
```css
.accordion-body {
  display: grid; 
  grid-template-rows: 0fr;
  transition: 250ms grid-template-rows ease;
}

.accordion:hover .accordion-body {
  grid-template-rows: 1fr;
}

.accordion-body > p {
  overflow: hidden;
}
```