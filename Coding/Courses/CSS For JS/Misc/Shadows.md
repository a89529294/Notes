There are three main ways to apply shadows in CSS: `box-shadow`, `text-shadow`, and `filter: drop-shadow`.

## box-shadow
When you apply `box-shadow` to an element, that element's box will cast a simulated shadow behind it.
```css
.card {
    box-shadow:
      2px 4px 8px hsl(0deg 0% 0% / 0.25);
}
```
`box-shadow` is most commonly called with 4 arguments:
1. Horizontal offset
2. Vertical offset
3. Blur radius
4. Color

## drop-shadow
```css
.card {
    filter: drop-shadow(
      2px 4px 8px hsl(0deg 0% 0% / 0.25)
    );
  }
```
it also accepts 4 values, of the same types, in the same order as `box-shadow`.
One thing to note is it produces a *softer, more blended shadow* since the third argument specifies a standard deviation.

## text-shadow
`text-shadow` is a shadow that applies only to the typography within the selected element.
```css
p {
    text-shadow:
      2px 4px 8px hsl(0deg 0% 0% / 1);
  }
```