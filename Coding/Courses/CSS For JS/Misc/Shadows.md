There are three main ways to apply shadows in CSS: `box-shadow`, `text-shadow`, and `filter: drop-shadow`.

## box-shadow
When you apply `box-shadow` to an element, that element's box will cast a simulated shadow behind it.
```css
.card {
    box-shadow:
      2px 4px 8px hsl(0deg 0% 0% / 0.25);
}
```
- `box-shadow` is most commonly called with 4 arguments:
	1. Horizontal offset
	2. Vertical offset
	3. Blur radius (>=0)
	4. Color
- it does accept one more argument, `spread` right after `blur`. It can take a negative or positive value, the bigger it is, the larger the shadow. 
- You can use `spread` to create a *one sided shadow*
```css
.bottom-shadow{
	box-shadow: 0px 12px 8px -8px hsl(0deg 0% 0% / 0.25);
}
```
- One more argument `inset`. This one must be specified as the first argument. It creates an *inner shadow*. 

## drop-shadow
```css
.card {
    filter: drop-shadow(
      2px 4px 8px hsl(0deg 0% 0% / 0.25)
    );
  }
```
- it also accepts 4 values, of the same types, in the same order as `box-shadow`.
- One thing to note is it produces a *softer, more blended shadow* since the third argument specifies a standard deviation.
- if we use `filter: drop-shadow` on an image that supports transparency (eg. png, gif, svg), the shadow will apply to the non-transparent parts of the image.
- When we apply `filter: drop-shadow` to an element, it contours that **element and all of its descendants** (even non-contiguous ones, like the smaller circle!), and applies the shadow to that shape.
- In summary, the `box-shadow` property applies a **shadow to an element's entire border box**, while the `drop-shadow` property only applies to the **visible content of an element**, which is why the latter requires content to be present.

## text-shadow
`text-shadow` is a shadow that applies only to the typography within the selected element.
```css
p {
    text-shadow:
      2px 4px 8px hsl(0deg 0% 0% / 1);
  }
```

## Designing Shadows
1. Each element on the page should be lit from the *same global light source*.
2. The `box-shadow` property represents the light source's position using *horizontal and vertical offsets*. To ensure consistency, each shadow should use the same ratio between these two numbers.
3. As an element gets closer to the user, the offset should increase, the blur radius should increase, and the shadow's opacity should decrease.
[shadow generator](https://www.joshwcomeau.com/shadow-palette/)