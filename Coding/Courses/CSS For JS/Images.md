- `img` is known as a "replaced element". Unlike other DOM nodes, the browser replaces the `<img>` tag with a foreign entity: the image itself.
- images are *inline* elements, and inline elements "go with the flow"; we generally can't give an inline element a `height`, since that would mess with the layout. And yet, *images can be given a height*.
- Images come with their own *intrinsic size*, based on the dimensions of the image file.
- `object-fit` & `object-position`

## object-fit
The **`object-fit`** CSS property sets how the content of a [replaced element](https://developer.mozilla.org/en-US/docs/Web/CSS/Replaced_element), such as an [`<img>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img) or [`<video>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video), should be resized to fit its container.
- `contain`: The replaced content is scaled to *maintain its aspect ratio* while *fitting within* the element's content box.
- `cover`: The replaced content is sized to *maintain its aspect* ratio while *filling the element's entire* content box. If the *object's aspect ratio does not match the aspect ratio of its box*, then the object will be *clipped to fit*. 
- `fill`: The replaced content is sized to *fill the element's content box*. The *entire object will completely fill the box*. If the object's aspect ratio does not match the aspect ratio of its box, then the object will be stretched to fit.
- `none`: The replaced content is not resized.
**Reminder** the `object-fit` property is specified on the `<img>` or `<video>` tags!

## object-position
The **`object-position`** CSS property specifies the alignment of the selected [replaced element](https://developer.mozilla.org/en-US/docs/Web/CSS/Replaced_element)'s contents within the element's box.
```css
img {
	object-position: 50% 50%; /* default value */
	object-position: left bottom;
}
```
- first percentage is the *horizontal offset*; second is the *vertical offset*. 
- percentage refers to width and height of element(`<img>` tag) itself

## images and flexbox
When dealing with images inside a `flex` container, often times it's just easier to wrap images in a `div` and set `img` to have `width:100%;`. Now the image wrappers are the flex items.

## picture element
```html
<picture>
  <source
    srcset="
      /cfj-mats/responsive-diamond.png 1x,
      /cfj-mats/responsive-diamond@2x.png 2x,
      /cfj-mats/responsive-diamond@3x.png 3x
    "
  />
  <img
    alt=""
    src="/cfj-mats/responsive-diamond.png"
  />
</picture>
```
- for styling, style the `<img>` tag.