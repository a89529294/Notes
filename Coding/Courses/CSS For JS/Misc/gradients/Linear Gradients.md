
![[output-onlinepngtools.png]]
- The above image shows the angle at `45deg`, default is `180deg`, which is equivalent to the keyword `to bottom`. The 45deg is measured against an invisible vertical line right through the center of the element.
- *Default is 180deg*, if you increase the value, gradient line rotates in the *clockwise direction*. If you decrease the value, gradient line rotates in the *counter-clockwise* direction. 
```css
/* from left ro right, the colors are equidistant by default, the percentages are not needed */
.my-class {
	background-image: linear-gradient(
      90deg,
      deeppink 0%,
      red 25%,
      coral 50%,
      gold 75%,
      white 100%
    );
}

/* now colors are no longer equidistant */
.my-class2 {
	background-image: linear-gradient(
      90deg,
      deeppink,
      red 10%,
      coral 20%,
      gold 30%,
      white
    );
}

/* sharp lines */
.my-class3 {
background-image: linear-gradient(
      90deg,
      deeppink 0%,
      deeppink 10%,
      red 10%,
      red 20%,
      coral 20%,
      coral 30%,
      gold 30%,
      gold 40%,
      white 40%
    );
}

/* gradient hints, by default this number is 50%, it tells the browser the midpoint between 2 colors */
.my-class4 {
background-image: linear-gradient(
      deeppink,
      80%,
      gold
    );
}
```