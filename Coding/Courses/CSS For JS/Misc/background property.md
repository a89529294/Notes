## background-origin
The **`background-origin`** [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) property sets the background's origin: from the border start, inside the border, or inside the padding. It takes three keyword values:
1. *border-box*: The background is positioned relative to the border box.
2. *padding-box*: The background is positioned relative to the padding box.
3. *content-box*: The background is positioned relative to the content box.
Note that `background-origin` is ignored when [`background-attachment`](https://developer.mozilla.org/en-US/docs/Web/CSS/background-attachment) is `fixed`.

## background-position
The **`background-position`** [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) property sets the initial position for each background image. The position is relative to the position layer set by [`background-origin`](https://developer.mozilla.org/en-US/docs/Web/CSS/background-origin). 

THe default is `0 0`, the top left corner.

Note using *absolute values vs percentages are very different*.
```css
/* this aligns the top left corner of the background image at the center of the element */
.class1 {
  width: 300px;
  height: 200px;
  background: radial-gradient(ellipse at center, #ff0000, #0000ff);
  background-size: 100% 100%;
  background-position: 150px 100px;
  background-repeat: no-repeat;
  border: 1px solid black;
}

/* this aligns the center of the background image at the center of the element */
.class2 {
	width: 300px;
	height: 300px;
	background-image: radial-gradient(ellipse at center, #ff0000, #0000ff);
	background-position: 50% 50%;
}
```

## background-image
You can apply **multiple backgrounds** to elements. These are layered atop one another with the *first background you provide on top* and the last background listed in the back. Only the last background can include a background color.
```css
.multi-bg{
	background-image: url(firefox.png), url(bubbles.png), linear-gradient(to right, rgba(30, 75, 115, 1), rgba(255, 255, 255, 0));
}
```